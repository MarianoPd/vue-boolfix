<template>
  <header class="container-fluid d-flex justify-content-between ">
    <img src="../assets/img/images.png" alt="logo">
    <div >
      <input v-model="search" type="text"
              @keyup.enter="sendSearch()" >
      <button @click="sendSearch()" >Search</button>
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
      search: '',
      
    }
  },
  methods:{
    sendSearch(){
      this.$emit('sendSearch', this.search);
      this.search = '';
    }  
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
