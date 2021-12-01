<template>
  <header class="container-fluid d-flex justify-content-between ">
    <img src="../assets/img/images.png" alt="logo">
    <div >
      <input v-model="movieSearch" type="text"
              @keyup.enter="sendResult()" >
      <button @click="sendResult()" >Search</button>
    </div>
  </header>
</template>

<script>
import axios from 'axios';
export default {
  
  name: 'Header',
  props: {
    
  },
  data(){
    return{
      movieSearch: '',
      movieSearchUrl: 'https://api.themoviedb.org/3/search/movie?api_key=b9d6f32d855fdb9b296cc4a18dc951e7&query=',
      results: [],
    }
  },
  methods:{
    sendResult(){
      this.getApi();
      this.$emit('sendResult', this.results);
      
    },
    
    getApi(){
        this.isLoaded = false;
        
        if(this.movieSearch !== ''){
          axios.get(this.movieSearchUrl + this.movieSearch)
            .then(r =>{
              this.isLoaded = true;
              this.results = r.data.results;
              this.movieSearch = '';
            })
            .catch( e => {
              console.log('axios error',e);
            })
        }
        
      },
  }
}
</script>


<style scoped lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';

header{
  height: 100px;
  background-color: black;
  img{
    height: 100%;
    margin-left: 20px;
  }
  input,button{
    margin-top: 30px;
    margin-right: 20px;
  }
  button{
    padding: 10px 20px;
  }
}
</style>
