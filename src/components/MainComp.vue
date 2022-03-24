<template>
<main>
  <div v-if="results.length > 0" class="container">
    <card-comp  v-for="result in results" :key="result.title" :result="result"></card-comp>
  </div>
  <div v-else class="container">
      <loader-comp></loader-comp>
  </div>
</main>
</template>

<script>
import CardComp from '../components/CardComp.vue';
import LoaderComp from '../components/LoaderComp.vue'

export default {
  name: 'MainComp',
  components:{
    CardComp,
    LoaderComp
  },
  props: {
    results: []
  }
}
</script>

<style scoped lang="scss">
  .container{
    width: 75%;
    margin: 0 auto;
    padding: 100px 0;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
  }
</style>
