<template>
  <div id="app">
    <Header @sendSearch="setMovieSearch"/>
    <Main :showMovieResult="movieResults" :showSerieResult="serieResults"/>
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
      serieResults: [],
      apiUrl: 'https://api.themoviedb.org/3/search',
      apiParams:{
        api_key: 'b9d6f32d855fdb9b296cc4a18dc951e7',
        language: 'it-IT',
        query: ''
      },
      isLoaded: false,
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
          axios.all([this.requestMovie(),this.requestSerie()])
            .then(axios.spread((movies, series) =>{
              this.isLoaded = true;
              this.movieResults = movies.data.results;
              this.serieResults = series.data.results;
              console.log(movies, series);            
            }))
            .catch( e => {
              console.log('axios error',e);
            })
        }
      },

      requestMovie(){
        return axios.get(this.apiUrl + '/movie',{params: this.apiParams});
      },
      requestSerie(){
        return axios.get(this.apiUrl + '/tv',{params: this.apiParams});
      }

  },
  computed:{
   

  }

}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';



</style>
