<template>
  <div id="app">
    <Header @sendSearch="setMovieSearch"/>
    <Main :showResult="movieResults"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
      movieResults: [],
      movieSearchUrl: 'https://api.themoviedb.org/3/search/movie',
      apiParams:{
        api_key: 'b9d6f32d855fdb9b296cc4a18dc951e7',
        language: 'it-IT',
        query: ''
      },
      isLoaded: true,
    }
  },
  methods:{
    setMovieSearch(text){
      this.apiParams.query = text;
      this.getApi();
      console.log('app result',this.apiParams.query);
    },
     getApi(){
        this.isLoaded = false;
        
        if(this.searchMovieString !== ''){
          axios.get(this.movieSearchUrl, {params: this.apiParams})
            .then(r =>{
              this.isLoaded = true;
              this.movieResults = r.data.results;
              console.log(r);            
            })
            .catch( e => {
              console.log('axios error',e);
            })
        }
      },
  },
  computed:{
   

  }

}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';



</style>
