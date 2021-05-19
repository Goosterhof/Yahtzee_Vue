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
  props: {
    scoreData: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      count: {},
      counts: {},
      countss: {},
      scores: [
        { id: 1, type: "Aces", points: null, locked: false },
        { id: 2, type: "Twos", points: null, locked: false },
        { id: 3, type: "Threes", points: null, locked: false },
        { id: 4, type: "Fours", points: null, locked: false },
        { id: 5, type: "Fives", points: null, locked: false },
        { id: 6, type: "Sixes", points: null, locked: false },
      ]

    }
  },
  mounted(){
    this.scoreData.forEach((i) => { this.count[i] = (this.count[i]||0) + 1 });

    Object.keys(this.count).forEach((item, i) => {
          this.counts = Object.values(this.count)[i] * Object.keys(this.count).map(Number)[i];
          this.countss = {[Object.keys(this.count).map(Number)[i]]: this.counts};
          console.log(this.countss);
      });
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
