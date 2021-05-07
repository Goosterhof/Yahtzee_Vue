<template>
  <div class="row w-50 m-auto">
    <div :class="{'toggle': toggle }"
        @click="toggleClass"
        v-for="die in die"
        :data-attribute="die"
        class="col text-center p-1" >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Die',
  data() {
    return {
      toggle: false,
      dieArr: [],
    }
  },
  computed:{
    die(){
    let die = [];
      for (var i = 0; i < 5; i++) {
        die[i] = Math.ceil(Math.random() * 6)
      }
      return die;
    }
  },
  methods: {
    toggleClass(event) {
       event.target.classList.toggle('toggle')
    }
  }


}
</script>

<style scoped>
  .toggle{
    box-shadow:0px -4px 0px -0px #000 inset;
    font-weight: 900;
  }
  .col{
    font-size: 70px
  }
  .col[data-attribute="1"]:after{
    content: '\2680';
  }
  .col[data-attribute="2"]:after{
    content: '\2681';
  }
  .col[data-attribute="3"]:after{
    content: '\2682';
  }
  .col[data-attribute="4"]:after{
    content: '\2683';
  }
  .col[data-attribute="5"]:after{
    content: '\2684';
  }
  .col[data-attribute="6"]:after{
    content: '\2685';
  }
</style>
