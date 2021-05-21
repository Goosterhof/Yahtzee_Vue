<template>
  <td
  :score="score"
   @click="toggleClass"
   class="text-center"
   data-bs-toggle="tooltip"
   data-bs-placement="right"
   title="Select to keep score">
 </td>
</template>

<script>
export default {
  name: 'Part',
  props: {
    score: {
      type: Object,
      default: false,
    }
  },
  methods: {
    toggleClass(event) {
      this.score.locked ? this.score.locked = false : this.score.locked = true
      event.target.classList.toggle('toggle')
    },
  }
}
</script>

<style scoped>
  .toggle{
    background: grey!important;
    color: #fff !important;
  }
  .text-center:hover{
    background-color: rgba(0, 0, 0, 0.2);
  }
</style>
