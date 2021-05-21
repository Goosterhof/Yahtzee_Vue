<template>
  <div class="row">
    <div class="col" v-for="die in dieArr">
      <Die class="die" :die="die"/>
    </div>
    <Button @btn-click="die" name="Throw" :disable="this.turns == 0 ? true : false"/>
    <p :turns="turns" class="text-center p-2">{{ turns }} Turns left</p>
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
      dieArr: [
        {value : undefined, locked: false},
        {value : undefined, locked: false},
        {value : undefined, locked: false},
        {value : undefined, locked: false},
        {value : undefined, locked: false},
      ],
    }
  },
  methods: {
    die(){
      for (let i = 0; i < 5; i++ ) {
        if (!this.dieArr[i].locked) {
          this.dieArr[i].value = Math.ceil(Math.random() * 6)
        }
      }
      this.turns -= 1;
      this.$emit('dieArr', this.dieArr)
      this.$emit('turns', this.turns)
    },


  }
}
</script>
