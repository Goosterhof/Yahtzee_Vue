<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col">
        <h3 class="text-center p-4">Yahtzee</h3>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <Die/>
        <Dice/>
        <Score/>
        <Button name="Throw"/>

      </div>
    </div>
  </div>
</template>

<script>
import Die from '../components/Die'
import Dice from '../components/Dice'
import Score from '../components/Score'
import Button from '../components/Button'


export default{
  components: {
    Die,
    Dice,
    Score,
    Button,

  }
}


</script>





<style scoped>

</style>
