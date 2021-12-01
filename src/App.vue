<template>
  <div id="app">
    <Header @sendResult="setResult"/>
    <Main :showResult="result"/>
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
      result: [],
    }
  },
  methods:{
    setResult(array){
      this.result = array;
      console.log('app result',this.result);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/vars.scss';
@import './assets/style/generals.scss';



</style>
