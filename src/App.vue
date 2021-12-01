<template>
  <div id="app">
    <Header @searchMovie="setSearch"/>
    <Main :searchCall="search"/>
  </div>
</template>

<script>
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
      search: '',
    }
  },
  methods:{
    setSearch(text){
      this.search = text;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';



</style>
