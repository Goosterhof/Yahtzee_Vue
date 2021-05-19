<template>
  <div class="col">

    <Dice @Scoreboard="click" />

    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end">
          <Button name="Score"/>
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
    <PartOne :scoreData="dieScore"/>
     <thead>
      <tr>
       <th scope="col">Part 2</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
     <PartTwo :scoreData="dieScore"/>
   </table>
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
      dieScore: []
    }
  },
  methods:{
    click(dieValues){
      dieValues.forEach((item, i) => {
        this.dieScore[i] = item.value
      });
      this.$emit('emitScore', this.dieScore)
    },
  }
}
</script>

<style scoped>
</style>
