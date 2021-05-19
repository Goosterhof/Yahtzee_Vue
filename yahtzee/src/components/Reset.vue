<template>
  <div class="col text-center">
    <Button @btn-click="resetGame" name="Next"/>
  </div>
</template>

<script>
import Button from './Button'
export default {
  name: 'Reset',
  components: {
    Button
  },
  props: {
    turn: String
  },
  data() {
    return {

    }
  },
  methods: {
    resetGame(){

    }
  },
}
</script>

<style scoped>

</style>
