<template>
  <div class="container-fluid">
    <div class="row w-50 m-auto">
      <div class="col">
        <h3 class="text-center p-4">Yahtzee</h3>
        <hr class="w-50 m-auto">
      </div>
    </div>
    <Dice/>
    
    <Turn/>
    <Scoreboard/>
  </div>
</template>

<script>
import Dice from '../components/Dice'
import Turn from '../components/Turn'
import Button from '../components/Button'
import Scoreboard from '../components/Scoreboard'


export default{
  components: {
    Dice,
    Turn,
    Button,
    Scoreboard,

  }
}


</script>

<style scoped>

</style>
