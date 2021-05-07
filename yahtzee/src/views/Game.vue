<template>
  <div class="container-fluid">
    <div class="row w-50 m-auto">
      <div class="col">
        <h3 class="text-center p-4">Yahtzee</h3>
        <hr class="w-50 m-auto">
      </div>
    </div>
    <Dice/>
    <Scoreboard/>
    <Reset/>
  </div>
</template>

<script>
import Dice from '../components/Dice'
import Reset from '../components/Reset'
import Button from '../components/Button'
import Scoreboard from '../components/Scoreboard'


export default{
  components: {
    Dice,
    Button,
    Reset,
    Scoreboard,
  },
  data() {
    return {
    }
  },
  methods: {
    getScore(){
      console.log('Get Score');
    },
  }
}


</script>

<style scoped>
#app .m-auto .row{
	clear:both;
	visibility:inherit;
}





</style>
