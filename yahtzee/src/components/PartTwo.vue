<template>
   <tbody>
    <tr v-for="score in scores"  >
     <td scope="row">{{score.type}}</td>
     <td
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
  name: 'PartTwo',
  props: {
    scoreData: Array,
  },
  data() {
    return {
      scores: [
        { id: 1, type: "Three of a Kind", points: null, locked: false },
        { id: 2, type: "Four of a Kind", points: null, locked: false  },
        { id: 3, type: "Full House", points: null, locked: false },
        { id: 4, type: "Small Straight", points: null, locked: false },
        { id: 5, type: "Large Straight", points: null, locked: false },
        { id: 6, type: "Yahtzee", points: null, locked: false },
        { id: 7, type: "Chance", points: null, locked: false  },
      ],
    }
  },
  methods: {
    toggleClass(event) {
       event.target.classList.toggle('toggle')
    },
  }
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
