<template>
<div class="row w-50 m-auto">
  <div class="col text-center">
    <p>{{ this.turns }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Turn',
  props: {
    turn: String
  },
  data() {
    return {
      turns: 3,
    }
  },
  methods: {
    turnsLeft(){

    }
  },
}
</script>

<style scoped>

</style>
