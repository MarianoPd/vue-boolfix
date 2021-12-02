<template>
  <main >
    <div class="container">
      <div class="text-center">
        <h1 v-if="showMovieResult.length === 0">There are no movies with this name</h1>
        <div v-else class="row flex-wrap ">
          <h1>Movies</h1>
          <Card  v-for="(result, index) in showMovieResult"
              :key="index"
              :sendResult="result"
              :type="'movie'"/>
        </div>
        <h1 v-if="showSerieResult.length === 0">There are no series with this name</h1>
        <div v-else class="row flex-wrap ">
          <h1>Series</h1>    
          <Card  v-for="(result, index) in showSerieResult"
              :key="index"
              :sendResult="result"
              :type="'serie'"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>

import Card from './Card.vue';
export default {
    name: 'Main',
    components:{
      Card,
    },
    props:{
      showMovieResult: Array,
      showSerieResult: Array,
    },
    data(){
      return{
        
      }
    },
    computed:{
      
    },
    methods:{
      
    }
    
}
</script>

<style scoped lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';


main{
    min-height: calc(100vh - 100px);
    background-color: $primary-color;
    h1{
      color: white;
      padding-top: 100px;
    }
}
</style>