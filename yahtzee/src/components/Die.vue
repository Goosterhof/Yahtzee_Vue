<template>
  <div class="row w-50 m-auto">
    <div :class="{'toggle': toggle }" @click="toggleClass" class="col text-center p-3 m-1" v-for="die in diceUni" v-html="die"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Die',
  data() {
    return {
      toggle: false
    }
  },
  computed:{
    diceUni(){
    let diceUni = [];
      for (var i = 0; i < 5; i++) {
        diceUni[i] = Math.ceil(Math.random() * 6)
      }
      return diceUni;
    }
  },
  methods: {
    toggleClass(event) {
       event.target.classList.toggle('toggle')
    }
  }


}
</script>

<style scoped>
  .toggle{
    border-bottom: 1px solid #000;
    text-decoration: bold;
  }
</style>
