<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col">
        <div class="dice" v-for="diceUni in diceSides"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Die',
  props: {
    name: name,
  },
  data() {
    return {
      diceSides: 6,
      diceUni: ['\u2680', '\u2681', '\u2682', '\u2683', '\u2684', '\u2685'],
    }
  },
  methods: {
    methodName(){

    }
  },
}
</script>

<style scoped>
.dice{
  width: 50px;
  height: 50px;
}
</style>
