<template>
<main>
  <card-comp v-for="result in results" :key="result.title" :result="result"></card-comp>
</main>
</template>

<script>
import CardComp from '../components/CardComp.vue';

export default {
  name: 'MainComp',
  components:{
    CardComp
  },
  props: {
    results: []
  }
}
</script>

<style scoped lang="scss">
  main{
    width: 75%;
    margin: 0 auto;
    padding: 100px 0;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
  }
</style>
