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
      onepoints: [],
      twopoints: [],
      turns: undefined,
      totalPoints: 0
    }
  },
  computed:{
    total(){
      let all = [this.onepoints, this.twopoints]
      all.forEach((item, i) => {
        if (all[i].locked) {
          console.log(all[i].points);
          this.totalPoints = Array.of(all[i].points.reduce((a, b) =>  a + b))
        }
      });



      // console.log( Object.assign(this.onepoints, this.two));
      // let all = [...this.onepoints, ...this.twopoints];
      // all.forEach((item, i) => {
      //   console.log(this.onepoints[i].points);
      //
      // });

    },
  },
  methods:{
    click(dieValues){dieValues.forEach((item, i) => {this.dieScore[i] = item.value})},
    pointsOne(value){this.onepoints = value},
    pointsTwo(value){this.twopoints = value},
    turn(value){this.turns = value},
    childScore(){
      this.$refs.PartOne.getScore()
      this.$refs.PartTwo.getScore()
    },
    nextGame(event){
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
    }
  }
}
</script>

<style scoped></style>
