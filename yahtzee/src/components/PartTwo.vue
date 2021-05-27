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
      count: {},
      scores: [
        { id: 1, type: "Three of a Kind", points: null, locked: false },
        { id: 2, type: "Four of a Kind", points: null, locked: false  },
        { id: 3, type: "Full House", points: null, locked: false },
        { id: 4, type: "Small Straight", points: null, locked: false },
        { id: 5, type: "Large Straight", points: null, locked: false },
        { id: 6, type: "Yahtzee", points: null, locked: false },
        { id: 7, type: "Chance", points: null, locked: false  },
      ]
    }
  },
  methods: {
    getScore(){
      this.scoreData.sort();
      this.scoreData.forEach((i) => {this.count[i] = (this.count[i]||0) + 1});
      const reducer = (b, d) => b + d,
            kind = (arr, num) => { return (arr.find(x => x === num))},
            house = (arr) => { return ((arr[0] === 2 && arr[1] === 3) || (arr[1] === 2 && arr[0] === 3)) },
            straight = (array, idx) => {
              let index = 1
              for (let i = 1; i < array.length; i++) {
                if (array[i] == array[i - 1] + 1)
                  index++;
                else
                  index = 1;
                if (index == idx)
                  return true;
              }
              return false;
            };

      for (let i = 0; i < this.scores.length; i++) {
        if (!this.scores[i].locked) {
          if (kind(Object.values(this.count), 3)) {this.scores[0].points = this.scoreData.reduce(reducer)};
          if (kind(Object.values(this.count), 4)) {this.scores[1].points = this.scoreData.reduce(reducer)};
          if (kind(Object.values(this.count), 5)) {this.scores[5].points = 50};
          if (house(Object.values(this.count))) {this.scores[2].points = 25};
          if (straight(this.scoreData, 4)) {this.scores[3].points = 30};
          if (straight(this.scoreData, 5)) {this.scores[4].points = 40};
          this.scores[6].points = this.scoreData.reduce(reducer);

        }
      }
      this.$emit('pointsTwo', this)
    },
  }
}
</script>

<style scoped>
</style>
