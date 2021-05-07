<template>
  <div class="row w-50 m-auto">
    <div class="col text-center">
      <Button @btn-click="resetGame"
            name="Reset"/>
    </div>
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
