<template>
  <div class="row w-50 m-auto">
    <div class="row">
      <div class="col" v-for="die in dieArr">
        <Die :die="die"/>
      </div>
    </div>
  <div class="row w-50 m-auto pt-5">
    <div class="col text-end">
      <Button @btn-click="die"
              :disable="this.turns == 0 ? true : false"
              name="Throw"
              />
      </div>
    <div class="col text-start">
      <p>{{ turns }} Turns left</p>
    </div>
    <hr>
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
      turns: 3,
      dieArr: [],
    }
  },
  methods: {
    die(){
      for (var i = 0; i < 5; i++) {
        this.dieArr.push(Math.ceil(Math.random() * 6))
      }
      this.turns -= 1;
    },
  },
}


</script>

<style scoped>
.disable{
  visibility:hidden;
}
</style>
