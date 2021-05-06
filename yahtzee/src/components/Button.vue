<template>
  <div class="container-fluid">
    <button @click="onClick()" class="btn btn-primary btn-sm" type="button">{{name}}</button>
  </div>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name: String
  },
  data() {
    return {
    }
  },
  methods: {
    onClick(){
      this.$emit('btn-click')
    }
  },
}
</script>

<style scoped>

</style>
