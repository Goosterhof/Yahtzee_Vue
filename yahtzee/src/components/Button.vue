<template>
  <button type="button" class="btn btn-outline-dark btn-sm" @click="onClick()" :disabled="disable">{{name}}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name: String,
    disable:{
      type: Boolean,
      default: false,
    }
  },
  methods: {
    onClick(){
      this.$emit('btn-click')
    }
  },
}
</script>
