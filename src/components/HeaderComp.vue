<template>
  <header>
    <img class="logo" src="../assets/logo.png" alt="logo" />
    <div class="selectors">
      <select
        class="selector"
        v-model="currentCategory"
        @change="$emit('catselect', currentCategory)"
      >
        <option value="All">Pick a genre</option>
        <option
          v-for="category in categories"
          :value="category"
          :key="category"
        >
          {{ category }}
        </option>
      </select>
      <select
        class="selector"
        v-model="currentAuthor"
        @change="$emit('autselect', currentAuthor)"
      >
        <option value="All">Pick an author</option>
        <option v-for="author in authors" :value="author" :key="author">
          {{ author }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  props: {
    categories: [],
    authors: [],
  },
  data() {
    return {
      currentCategory: "All",
      currentAuthor: "All",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  height: 80px;
  background-color: rgb(48, 58, 69);
  padding: 15px;
  display: flex;
  justify-content: space-between;

  .logo {
    height: 100%;
  }

  .selector {
    width: 200px;
    font-size: 1.1rem;
    height: 100%;
    margin: 0 5px;
  }

}
</style>
