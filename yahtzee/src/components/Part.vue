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
      // TODO :: next line can be rewritten to this.score.locked = !this.score.locked
      this.score.locked ? this.score.locked = false : this.score.locked = true
      // TODO :: no need to toggle this this way, it can be done the Vue way with :class={keep:this.score.locked} in the td in the template
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
