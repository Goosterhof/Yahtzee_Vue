<template>
    <button
      @click="onClick()"
      class="btn btn-outline-dark btn-sm"
      type="button"
      :disabled="disable"
      >{{name}}
    </button>
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
