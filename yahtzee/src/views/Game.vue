<template>
  <div class="container-fluid">
    <div class="row w-50 m-auto">
      <div class="col">
        <h3 class="text-center p-4">Yahtzee</h3>
        <hr>
        <Scoreboard/>
      </div>
    </div>
  </div>
</template>

<script>
// TODO :: Dice and Button component aren't used here, can be deleted
import Dice from '../components/Dice'
import Button from '../components/Button'
import Scoreboard from '../components/Scoreboard'
export default{
  components: {
    Dice,
    Button,
    Scoreboard,
  }
}
</script>

<style scoped>
</style>
