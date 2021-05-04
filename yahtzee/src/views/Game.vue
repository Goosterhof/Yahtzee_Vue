<template>
  <div class="container-fluid">
    <div class="row w-50 m-auto">
      <div class="col">
        <h3 class="text-center p-4">Yahtzee</h3>
        <hr class="w-50 m-auto">
      </div>
    </div>

    <Dice/>


    <Score/>


  </div>
</template>

<script>
import Dice from '../components/Dice'
import Score from '../components/Score'
import Button from '../components/Button'


export default{
  components: {
    Dice,
    Score,
    Button,

  }
}


</script>





<style scoped>

</style>
