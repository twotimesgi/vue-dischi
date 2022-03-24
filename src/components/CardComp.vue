<template>
  <div class="card">
    <img :src="result.poster">
    <h2> {{ result.title }} </h2>
    <h3> {{ result.author }} </h3>
    <h4> {{ result.year }} </h4>
  </div>
</template>

<script>
export default {
  name: 'CardComp',
  props: {
    result: Object
  }
}
</script>

<style scoped lang="scss">
  .card{
    width: calc(100% / 5 - 20px);
    min-width: 150px;
    background-color: rgb(48, 58, 69);
    padding: 10px;
    text-align: center;


    img{
      width: 100%;
    }

    h2{
      color: white;
      text-transform: uppercase;
      font-size: 1.1rem;
      margin-top: 20px;
    }

    h3, h4{
      opacity: 0.7;
      font-weight: normal;
    }

    h3{
      font-size: 0.9rem;
      margin-top: 20px;
    }

    h4{
      font-size: 0.8rem;
    }
  }


</style>
