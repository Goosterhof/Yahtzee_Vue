<template>
  <div class="col">
    <Dice @dieArr="click"
          @turns="turn"
          ref="emptyDie"
    />
    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end">
          <Button
            name="Score"
            :key="reset"
            :disable="this.turnsValue == 0 ? false : true"
            @btn-click="childScore()"
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
      <PartOne :scoreData="dieScore" ref="PartOne" />
      <thead>
        <tr>
          <th scope="col">Part 2</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <PartTwo :scoreData="dieScore" ref="PartTwo" />
    </table>

    <table class="table table-sm">
  <thead>
    <tr>
    <th>Totals</th>
    <th :total="total"></th>
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
      turnsValue: undefined,
    }
  },
  watch:{
    handler: 'total',
    immediate: true
  },
  methods:{
    click(dieValues){
      console.log(dieValues);
      dieValues.forEach((item, i) => {this.dieScore[i] = item.value});
      this.$emit('emitScore', this.dieScore)
    },
    turn(value){
      this.turnsValue = value
    },
    childScore(){
      this.$refs.PartOne.getScore()
      this.$refs.PartTwo.getScore()
    },
    total(){

    },
    nextGame(){
      const ref = this.$refs.emptyDie;
      for (let i = 0; i < ref.dieArr.length; i++) {
        ref.dieArr.locked = false
      }
      Object.assign(ref.$data, ref.$options.data());

      const one = this.$refs.PartOne;
        for (let i = 0; i < one.scores.length; i++) {
          if (!one.scores[i].locked) {
            one.scores[i].points = null
          }
        }
      const two = this.$refs.PartTwo;
        for (let i = 0; i < two.scores.length; i++) {
          if (!two.scores[i].locked) {
            two.scores[i].points = null
          }
        }

      this.buttonKey++

    }
  }
}
</script>

<style scoped></style>
