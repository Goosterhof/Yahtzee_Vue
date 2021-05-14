<template>
   <tbody>
    <tr v-for="score in scores"  >
     <td scope="row">{{score.type}}</td>
     <td
      :class="{'toggle': toggle }"
      @click="toggleClass"
      class="text-center"
      data-bs-toggle="tooltip"
      data-bs-placement="right"
      title="Select to keep score">{{score.points}}</td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: 'ScorePartTwo',
  props: {
    name: String,
    value: String,
  },
  data() {
    return {
      scores: [
        { id: 1, type: "Three of a Kind", points: null },
        { id: 2, type: "Four of a Kind", points: null },
        { id: 3, type: "Full House", points: null },
        { id: 4, type: "Small Straight", points: null },
        { id: 5, type: "Large Straight", points: null },
        { id: 6, type: "Yahtzee", points: null },
        { id: 7, type: "Chance", points: null },
      ],
      toggle: false
    }
  },
  methods: {
    toggleClass(event) {
       event.target.classList.toggle('toggle')
    }
  },
}
</script>

<style scoped>
  .toggle{
    background: grey!important;
    color: #fff !important;
  }
  .text-center:hover{
  background-color: rgba(0, 0, 0, 0.2);
  }

</style>
