<template>
  <div class="col">
    <Dice @Scoreboard="click" @turns="turn" />
    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end">
          <Button
            name="Score"
            @btn-click="childScore()"
            :disable="this.turnValue == 0 ? false : true"
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
    <div class="col text-center">
      <Button @btn-click="nextGame" name="Next" />
    </div>
  </div>
</template>

<script>
import Dice from './Dice'
import Button from './Button'
import PartOne from './PartOne'
import PartTwo from './PartTwo'
export default {
  name: 'Scoreboard',
  components: {
    Dice,
    Button,
    PartOne,
    PartTwo
  },
  data() {
    return {
      dieScore: [],
      turnValue: undefined
    }
  },
  methods:{
    click(dieValues){
      dieValues.forEach((item, i) => {
        this.dieScore[i] = item.value
      });
      this.$emit('emitScore', this.dieScore)
    },
    turn(value){
      this.turnValue = value
    },
    childScore(){
      this.$refs.PartOne.getScore()
      this.$refs.PartTwo.getScore()
    },
    nextGame(){
    
    }
  }
}
</script>

<style scoped></style>
