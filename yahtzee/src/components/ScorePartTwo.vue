<template>
   <tbody>
    <tr v-for="list in scores" >
     <td scope="row" >{{name}}</td>
     <td
      :class="{'toggle': toggle }"
      @click="toggleClass"
      class="text-center"
      data-bs-toggle="tooltip"
      data-bs-placement="right"
      title="Select to keep score">{{value}}</td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: 'ScorePartTwo',
  props: {
    name: String,
    value: String,
  },
  data() {
    return {
      scores: 6,
      toggle: false
    }
  },
  methods: {
    toggleClass(event) {
       event.target.classList.toggle('toggle')
    }
  },
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
