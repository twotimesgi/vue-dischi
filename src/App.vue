<template>
  <div id="app">
    <header-comp></header-comp>
    <main-comp :results="results"></main-comp>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
import axios from "axios";



export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return {
      results: []
    }
  },
  created(){
    axios.request("https://flynn.boolean.careers/exercises/api/array/music").then((req)=>{
      this.results = req.data.response;
  })
  }
}
</script>

<style lang="scss">
*{
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

body{
  background-color: rgb(33, 45, 58);
}
</style>
