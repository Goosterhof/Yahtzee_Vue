<template>
  <div :die="die.value"
       @click="toggleClass"
       class="col text-center p-1"></div>
</template>

<script>
export default {
  name: 'Die',
  props: {
    die: {
      type: Object,
      required: true,
    }
  },
  methods: {
    toggleClass(event) {
      this.die.locked ? this.die.locked = false : this.die.locked = true
      event.target.classList.toggle('keep')
    },
  }
}
</script>

<style scoped>
  .keep{
    box-shadow:0px -4px 0px -0px #000 inset;
    font-weight: 700;
  }
  .col{
    font-size: 50px
  }
  .col[die="1"]:after{
    content: '\2680';
  }
  .col[die="2"]:after{
    content: '\2681';
  }
  .col[die="3"]:after{
    content: '\2682';
  }
  .col[die="4"]:after{
    content: '\2683';
  }
  .col[die="5"]:after{
    content: '\2684';
  }
  .col[die="6"]:after{
    content: '\2685';
  }
</style>
