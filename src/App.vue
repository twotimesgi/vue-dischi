<template>
  <div id="app">
    <header-comp
      @catselect="filterByCategory"
      :categories="categories"
    ></header-comp>
    <main-comp :results="filteredResults"></main-comp>
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
      filteredResults: [],
      results: [],
      categories: [],
    };
  },
  created() {
    setTimeout(() => {
      //Forzo un ritardo nel caricamento dei dati
      axios
        .request("https://flynn.boolean.careers/exercises/api/array/music")
        .then((req) => {
          this.results = req.data.response;
        })
        .then(() => {
          this.results.forEach((result) => {
            if (!this.categories.includes(result.genre))
              this.categories.push(result.genre);
          });
        })
        .then(() => {
          this.filteredResults = this.results;
        });
    }, 2000);
  },
  methods: {
    filterByCategory(cat) {
      this.filteredResults = this.results.filter((res) => res.genre == cat || cat == "All");
    },
  },
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
