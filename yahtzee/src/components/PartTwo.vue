<template>
   <tbody>
    <tr v-for="score in scores">
     <td scope="row">{{score.type}}</td>
     <Part :score="score" v-html="score.points"/>
    </tr>
  </tbody>
</template>

<script>
import Part from './Part'
export default {
  name: 'PartTwo',
  components: {
    Part
  },
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
    getScore(){
      this.scoreData.sort();
      let reducer = (a, c) => a + c,
          aKind = (a, c) => a.filter(x => a.filter(b => b === x).length === c);
          if (!this.scores.locked) {

            this.scores[0].points = aKind(this.scoreData, 3),
            this.scores[1].points = aKind(this.scoreData, 4),
            this.scores[5].points = aKind(this.scoreData, 5);

      }
    },
  }
}
</script>

<style scoped>
</style>
