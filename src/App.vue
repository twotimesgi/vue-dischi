<template>
  <div id="app">
    <header-comp
      @autselect="filterByAuthor" @catselect="filterByCategory"
      :categories="categories" :authors="authors"
    ></header-comp>
    <main-comp :results="filtered" :loaded="dataLoaded"></main-comp>
  </div>
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },
  data() {
    return {
      results: [],
      categories: [],
      authors: [],
      dataLoaded: false,
      filters: {
        category: "All",  
        author: "All"
      }
    };
  },
  created() {
    setTimeout(() => {
      //Forzo un ritardo nel caricamento dei dati
      axios
        .request("https://flynn.boolean.careers/exercises/api/array/music")
        .then((req) => {
          this.results = req.data.response;
          this.dataLoaded = true;
        })
        .then(() => {
          this.results.forEach((result) => {
            if (!this.categories.includes(result.genre))
              this.categories.push(result.genre);
          });
          this.results.forEach((result) => {
            if (!this.authors.includes(result.author))
              this.authors.push(result.author);
          });
        })
    }, 2000);
  },
  methods: {
    filterByCategory(cat) {
      this.filters.category = cat;
    },
    filterByAuthor(aut) {
      this.filters.author = aut;
    },
  },
  computed:{
    filtered(){
      return this.results.filter((res) => (res.genre == this.filters.category || this.filters.category == "All")&&(res.author == this.filters.author || this.filters.author == "All"));
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

body {
  background-color: rgb(33, 45, 58);
  font-family: "Roboto", sans-serif;
  color: white;
}
</style>
