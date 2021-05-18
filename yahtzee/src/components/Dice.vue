<template>A
  <div class="row">
    <div class="col" v-for="die in dieArr">
      <Die class="die" :die="die" :toggle="toggle" />
    </div>
    <Button @btn-click="die" name="Throw" :disable="this.turns == 0 ? true : false" />
    <p class="text-center p-2">{{ turns }} Turns left</p>
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
  data(){
    return {
      turns: 3,
      dieArr: [],
    }
  },
  computed:{
  },
  methods: {
    die(){
      if (!this.toggle || undefined) {
        for (let i = 0; i < 5; i++ ) {
        this.dieArr[i] = Math.ceil(Math.random() * 6)
        }
      }
      this.turns -= 1;
    },
  }
}
</script>

<style scoped>
</style>
