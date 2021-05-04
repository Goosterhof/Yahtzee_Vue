<template>
  <div class="container-fluid">
    <button class="btn btn-primary" type="button" name="button">{{name}}</button>
  </div>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name: name
  },
  data() {
    return {
    }
  },
  methods: {
    methodName(){

    }
  },
}
</script>

<style scoped>

</style>
