<template>
  <main >
    <div class="container">
      <div v-if="(showMovieResult.length !== 0) || (showSerieResult.length !== 0)">
        <h1><strong>Movies</strong></h1>
        <h1 v-if="showMovieResult.length === 0">There are no movies with this name</h1>
        <div v-else class="row flex-wrap no-gutters mb-1">
          <Card  v-for="(result, index) in showMovieResult"
              :key="index"
              :sendResult="result"
              :type="'movie'"/>
        </div>
        <h1><strong>Series</strong></h1>
        <h1 v-if="showSerieResult.length === 0">There are no series with this name</h1>
        <div v-else class="row flex-wrap no-gutters mb-1">    
          <Card  v-for="(result, index) in showSerieResult"
              :key="index"
              :sendResult="result"
              :type="'serie'"/>
        </div>        
      </div>
      <h1 v-else>No sesults</h1>
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
    background-image: linear-gradient($primary-color, darken($primary-color,10%));
    h1{
      color: white;
      padding-top: 100px;
    }
}
</style>