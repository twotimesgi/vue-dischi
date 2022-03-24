<template>
<header>
  <img class="logo" src='../assets/logo.png' alt="logo">
  <select class="category-selector">
    <option value="All">All</option>
  </select>
</header>
</template>

<script>
export default {
  name: 'HeaderComp',
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
    min-width: 100px;
  }
}
</style>
