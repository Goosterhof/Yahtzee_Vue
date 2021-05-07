<template>
  <div class="row w-25 m-auto mt-5">
    <table class="table table-sm">
      <tr>
        <td><h6>Scoreboard</h6></td>
        <td class="text-end"><Button @btn-click="$emit('getScore')" name="Score"/></td>
      </tr>
  </table>
    <hr>
    <table class="table table-sm">
     <thead>
      <tr>
       <th scope="col">Part 1</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
    <ScorePartOne name="ScoreName" value="5"/>
     <thead>
      <tr>
       <th scope="col">Part 2</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
     <ScorePartTwo name="ScoreName" value="5"/>
   </table>
  </div>
</template>

<script>
import ScorePartOne from './ScorePartOne'
import ScorePartTwo from './ScorePartTwo'
import Button from './Button'
export default {
  name: 'Scoreblock',
  components: {
    ScorePartOne,
    ScorePartTwo,
    Button
  },
  data() {
    return {

    }
  },
  methods: {
    methodName(){

    }
  },
}
</script>

<style scoped>

</style>
