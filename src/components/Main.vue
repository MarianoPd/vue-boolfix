<template>
  <main >
    <div class="container">
      <div class="row flex-wrap">
        <Card/>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue'
export default {
    name: 'Main',
    components:{
      Card,
    },
    props:{
      searchCall: String,
    },
    data(){
      return{
        apiUrl: 'https://api.themoviedb.org/3/movie/550',
        result: [],
        isLoaded: false,
      }
    },
    computed:{
      searchMovie(){

        return 0;
      }
    },
    methods:{
      getApi(){
      this.isLoaded = true;
      
      axios.get(this.apiUrl )
      .then(r =>{
        console.log(r.data);
        
      })
      .catch( e => {
        console.log(e);
      })
    },
    }
    
}
</script>

<style scoped lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';


main{
    height: calc(100vh - 100px);
    background-color: $primary-color;
}
</style>