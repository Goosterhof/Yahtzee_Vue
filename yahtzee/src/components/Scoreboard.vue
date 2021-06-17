<template>
  <div class="col">
    <Dice @dieArr="click"
          @turns="turn"
          ref="Dice"
    />
    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end">
          <!-- TODO :: no need for the ? false : true, just add a !  -->
          <Button
            name="Score"
            :key="reset"
            :disable="this.turns == 0 ? false : true"
            @btn-click.once="childScore"
          />
        </td>
      </tr>
    </table>
    <table class="table table-sm">
      <thead>
        <tr>
          <th scope="col">Part 1</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <PartOne :scoreData="dieScore" @emitToScoreboard="getScores($event, 'scoreOne')" ref="PartOne" />
      <thead>
        <tr>
          <th scope="col">Part 2</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <PartTwo :scoreData="dieScore" @emitToScoreboard="getScores($event, 'scoreTwo')" ref="PartTwo" />
    </table>

    <table class="table table-sm">
  <thead>
    <tr>
    <th>Totals</th>
    <th class="text-center">{{totalPoints}}</th>
    </tr>
  </thead>
    </table>
    <div class="col text-center">
      <Button @btn-click="nextGame" name="Next" />
    </div>
  </div>
</template>

<script>
import Dice from './Dice'
import Part from './Part'
import Button from './Button'
import PartOne from './PartOne'
import PartTwo from './PartTwo'
export default {
  name: 'Scoreboard',
  components: {
    Dice,
    Part,
    Button,
    PartOne,
    PartTwo
  },
  data() {
    return {
      reset: 1,
      dieScore: [],
      scores: [],
      turns: undefined,
      fromChild: [],
      totalPoints: 0
    }
  },
  methods:{
    turn(value, name){this.turns = value},
    click(dieValues){dieValues.forEach((item, i) => {this.dieScore[i] = item.value})},
    childScore(value){
      this.$refs.PartOne.getScore()
      this.$refs.PartTwo.getScore()
    },
    getScores(value, part){
      value.forEach((item, i) => {
        if (item.locked) {
          this.fromChild.push(item.points)
        }
      });
      this.totalPoints = this.fromChild.reduce((a,b) => a + b)
    },
    nextGame(){
      let die = this.$refs.Dice,
          one = this.$refs.PartOne,
          two = this.$refs.PartTwo;
      for (let i = 0; i < die.dieArr.length; i++) {
        die.dieArr[i].locked = false
        die.dieArr[i].value = undefined
        die.$children[i].$el.classList.remove('keep')
      }
      for (let i = 0; i < one.scores.length; i++) {
        if (!one.scores[i].locked) {
          one.scores[i].points = null
        }
      }
      for (let i = 0; i < two.scores.length; i++) {
        if (!two.scores[i].locked) {
          two.scores[i].points = null
        }
      }
      die.turns = 3
      one.count = {}
      one.counts = {}
      two.count = {}
      this.dieScore = []
      this.fromChild = []
      this.turnsValue = undefined
      this.reset++
    }
  }
}
</script>

<style scoped></style>
