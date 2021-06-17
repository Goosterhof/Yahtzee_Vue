<template>
   <tbody>
    <tr v-for="score in scores">
      <!-- TODO :: why the v-model here? -->
     <td v-model="score.points" scope="row">{{score.type}}</td>
     <!-- TODO :: it's cleaner to show the points in the Part component -->
     <Part :score="score" v-html="score.points"/>
    </tr>
  </tbody>
</template>

<script>
import Part from './Part';
export default {
  name: 'PartOne',
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
      count: {},
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
  methods: {
    getScore(){
      this.scoreData.forEach((i) => {this.count[i] = (this.count[i]||0) + 1});
      const counts = {};

      Object.keys(this.count).forEach((item, i) => {
        // TODO :: can be this.count[item] * item, then we cond't need i above
        const count = Object.values(this.count)[i] * item;
        counts [item] = count
        
        // TODO :: can use forof loop
        for (let i = 0; i < this.scores.length; i++) {
          if (!this.scores[i].locked) {
            if (item == this.scores[i].id) {
              this.scores[i].points = count;
            }
          }
        }
      });
      this.$emit('emitToScoreboard', this.scores)
    },
  }
}
</script>
