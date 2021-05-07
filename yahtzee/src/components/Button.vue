<template>
  <div class="container-fluid">
    <button
      @click="onClick()"
      class="btn btn-primary btn-sm"
      type="button"
      :disabled="disable"
      >{{name}}</button>
  </div>
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
