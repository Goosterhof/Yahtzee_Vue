<template>
  <div class="row w-50 m-auto">
    <div class="col" v-for="diceUni  in diceUni" >

      <a class="unicode"> {{diceUni(diceUni)}} </a>

    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Die',
  data() {
    return {
      diceFace: 6,
    }
  },
  computed:{
    diceUni(){
      let diceUni = [];
      for (var i = 0; i < 5; i++) {
        diceUni.push(` "\\u268${Math.ceil(Math.random() * 6 )}\" `)
      }
      console.log(diceUni);
      return diceUni
    }
  },
}
</script>

<style scoped>
  .unicode{
  	font-size:70px;
    text-align:center;
    text-decoration: none;
    color: black
  }
</style>
