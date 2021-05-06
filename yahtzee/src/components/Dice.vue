<template>
  <div class="row w-50 m-auto">
    <div class="col text-center">


      <Die/>

      <div class="btn-group mt-3" role="group">
        <Button @btn-click="throwIt"  name="Throw"/>
        <Button @btn-click="getScore" name="Score"/>
      </div>
  </div>
</div>
</template>


<script>
import Die from './Die'
import Button from './Button'

export default {
  name: 'Dice',
  components: {
    Die,
    Button
  },
  data() {
    return {
      diceAmount: 5,
      die: Die
    }
  },
  computed: {
  },


  methods: {
    throwIt(){
      return this.die;
    },
    getScore(){
      console.log('Get Score');
    },
    log(){
      console.log(Die.computed);
    },
  },
}
</script>

<style scoped>
</style>
