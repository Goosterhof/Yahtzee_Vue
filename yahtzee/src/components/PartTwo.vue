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
  name: 'PartTwo',
  props: {
    scoreData: {
      type: Array,
      required: true
    }
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
    toggleClass(event){
       event.target.classList.toggle('toggle')
    },
    getScore(){
      this.scoreData.sort();
      let reducer = (a, c) => a + c,
          aKind = (a, c) => a.filter(x => a.filter(b => b === x).length === c),
          aKind3 = aKind(this.scoreData, 3),
          aKind4 = aKind(this.scoreData, 4),
          aKind5 = aKind(this.scoreData, 5);
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
