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
      genreMovieList: [],
      genreTvList: [],
      apiUrl: 'https://api.themoviedb.org/3/search',
      popularApiUrl: 'https://api.themoviedb.org/3/discover',
      genreListUrl: 'https://api.themoviedb.org/3/genre',
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
      this.getApi(this.apiUrl);
      console.log('app result',this.apiParams.query);
    },
    getApi(url){
      this.isLoaded = false;
      
      if(this.searchMovieString !== ''){
        axios.all([this.requestMovie(url),this.requestSerie(url)])
          .then(axios.spread((movies, series) =>{
            this.isLoaded = true;
            this.movieResults = movies.data.results;
            this.serieResults = series.data.results;
            console.log('axios results',movies, series);            
          }))
          .catch( e => {
            console.log('axios error',e);
          })
      }
    },

    requestMovie(url){
      return axios.get(url + '/movie',{params: this.apiParams});
    },
    requestSerie(url){
      return axios.get(url + '/tv',{params: this.apiParams});
    },

    getGenresApi(url){
      axios.all([this.requestMovieGenres(url),this.requestTvGenres(url)])
        .then(axios.spread((moviesGen, seriesGen) =>{
          this.genreMovieList = moviesGen.data.genres;
          this.genreTvList = seriesGen.data.genres;
          console.log('list genre',this.genreMovieList,this.genreTvList);
        }))
        .catch( e => {
            console.log('axios error list',e);
        })
    },
    requestMovieGenres(url){
      return axios.get(url + '/movie/list',{params: this.apiParams});
    },
    requestTvGenres(url){
      return axios.get(url + '/tv/list',{params: this.apiParams});
    },

  },
  mounted(){
    this.getApi(this.popularApiUrl);
    this.getGenresApi(this.genreListUrl);
  }

}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';



</style>
