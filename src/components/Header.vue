<template>
  <header class="container-fluid d-flex justify-content-between ">
    <img src="../assets/img/images.png" alt="logo">
    <div >
      <input v-model="movieSearch" type="text" >
      <button @click="$emit('searchMovie', movieSearch)" >invio</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    
  },
  data(){
    return{
      movieSearch: '',
    }
  },
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
}
</style>
