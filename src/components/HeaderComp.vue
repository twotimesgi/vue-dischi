<template>
<header>
  <img class="logo" src='../assets/logo.png' alt="logo">
  <select class="category-selector" v-model="currentCategory" @change="$emit('catselect', currentCategory)">
    <option value="All">Pick a genre</option>
    <option v-for="category in categories" :value="category" :key="category">{{ category }}</option>
  </select>
</header>
</template>

<script>
export default {
  name: 'HeaderComp',
  props:{
    categories: [],
  },
  data(){
    return{
        currentCategory: "All",
    }
  }
}
</script>

<style scoped lang="scss">
header{
  height: 80px;
  background-color: rgb(48, 58, 69);
  padding: 15px;
  display: flex;
  justify-content: space-between;

  .logo{
    height: 100%;
  }

  .category-selector{
    width: 300px;
    font-size: 1.1rem;
  }
}
</style>
