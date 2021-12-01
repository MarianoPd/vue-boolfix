<template>
  <div id="app">
    <Header @sendSearch="setMovieSearch"/>
    <Main :showResult="results"/>
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
      searchMovieString: '',
      results: [],
      movieSearchUrl: 'https://api.themoviedb.org/3/search/movie?api_key=b9d6f32d855fdb9b296cc4a18dc951e7&query=',
      isLoaded: true,
    }
  },
  methods:{
    setMovieSearch(text){
      this.searchMovieString = text;
      this.getApi();
      console.log('app result',this.searchMovieString);
    },
     getApi(){
        this.isLoaded = false;
        
        if(this.searchMovieString !== ''){
          axios.get(this.movieSearchUrl + this.searchMovieString)
            .then(r =>{
              this.isLoaded = true;
              this.results = r.data.results;
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
