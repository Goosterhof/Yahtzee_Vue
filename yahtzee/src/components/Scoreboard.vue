<template>
  <div class="col">
    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end">
          <Button name="Score" @btn-click="click"/>
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
    <PartOne/>
     <thead>
      <tr>
       <th scope="col">Part 2</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
     <PartTwo/>
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
      dieValues: this.$root.$on('payload')
    }
  },
  methods:{
    click(value){
        console.log(this.dieValues);
    }
  }
}
</script>

<style scoped>
</style>
