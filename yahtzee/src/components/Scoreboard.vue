<template>
  <div class="row w-25 m-auto mt-5">
    <h6 class="text-center">Scoreboard</h6>
    <hr>
    <table class="table table-sm">
     <thead>
      <tr>
       <th scope="col">Part 1</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
      <ScorePartOne name="name" value="5"/>
     <thead>
      <tr>
       <th scope="col">Part 2</th>
       <th scope="col" class="text-center">#</th>
      </tr>
     </thead>
     <ScorePartTwo name="name" value="5"/>
   </table>
  </div>
</template>

<script>
import ScorePartOne from './ScorePartOne'
import ScorePartTwo from './ScorePartTwo'
export default {
  name: 'Scoreblock',
  components: {
    ScorePartOne,
    ScorePartTwo
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
