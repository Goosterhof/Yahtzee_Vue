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
      <PartOne :scoreData="dieScore" @pointsOne="pointsOne" ref="PartOne" />
      <thead>
        <tr>
          <th scope="col">Part 2</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <PartTwo :scoreData="dieScore" @pointsTwo="pointsTwo" ref="PartTwo" />
    </table>

    <table class="table table-sm">
  <thead>
    <tr>
    <th>Totals</th>
    <th class="text-right" :total="total">{{totalPoints}}</th>
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
      onepoints: {},
      twopoints: {},
      turns: undefined,
      totalPoints: 0
    }
  },
  computed:{
    total(){

    },
  },
  methods:{
    click(dieValues){dieValues.forEach((item, i) => {this.dieScore[i] = item.value})},
    turn(value){this.turns = value},
    pointsOne(value){this.onepoints = value},
    pointsTwo(value){this.twopoints = value},
    childScore(){
      this.$refs.PartOne.getScore()
      this.$refs.PartTwo.getScore()
    },
    nextGame(event){
      console.log(this.allpoints);
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
      this.turnsValue = undefined
      this.reset++
      [...this.onepoints, ...this.twopoints].forEach((item, i) => {
        console.log(item.points);

        this.totalPoints = item.points.reduce(function (accumulator, currentValue) {
          return accumulator + currentValue
        })
      });
    }
  }
}
</script>

<style scoped></style>
