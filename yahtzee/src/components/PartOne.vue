<template>
   <tbody>
    <tr v-for="score in scores">
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
  name: 'PartOne',
  data() {
    return {
      scores: [
        { id: 1, type: "Aces", points: null, locked: false},
        { id: 2, type: "Twos", points: null, locked: false},
        { id: 3, type: "Threes", points: null, locked: false},
        { id: 4, type: "Fours", points: null, locked: false},
        { id: 5, type: "Fives", points: null, locked: false},
        { id: 6, type: "Sixes", points: null, locked: false},
      ]
    }
  },
  mounted() {
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
  tbody{
    font-size: 15px;
  }

</style>
