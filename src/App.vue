<template>
  <div id="app">
    <header-comp :categories="categories"></header-comp>
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
      results: [],
      categories: []
    }
  },
  created(){
    axios.request("https://flynn.boolean.careers/exercises/api/array/music").then((req)=>{
      setTimeout(()=> this.results = req.data.response,2000);
  }).then(()=>{
    this.results.forEach((result)=>{
      if(!this.categories.includes(result.genre)) this.categories.push(result.genre);
    })
  });
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
  *{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
  }

  body{
    background-color: rgb(33, 45, 58);
    font-family: 'Roboto', sans-serif;
    color: white;
  }
</style>
