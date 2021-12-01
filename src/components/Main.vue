<template>
  <main >
    <div class="container">
      <div class="row flex-wrap text-center">
        <h1 v-if="showResult.length === 0">There are no results</h1>
        <Card v-else v-for="(result, index) in showResult"
              :key="index"
              :sendResult="result"/>
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
      showResult: Array,
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