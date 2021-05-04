<template>
  <div class="row w-50 m-auto">
    <div class="col">
      <Die/>
  </div>
</div>
</template>


<script>
import Die from '../components/Die'
import Button from '../components/Button'

export default {
  name: 'Dice',
  components: {
    Die,
    Button
  },
  data() {
    return {
      diceAmount: 5,
    }
  },
  methods: {
    methodName(){

    }
  },
}
</script>

<style scoped>

</style>
