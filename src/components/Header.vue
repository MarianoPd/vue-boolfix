<template>
  <header>
    <img src="../assets/img/images.png" alt="logo">
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    
  }
}
</script>


<style scoped lang="scss">
@import '../assets/style/generals.scss';
@import '../assets/style/vars.scss';

header{
  height: 100px;
  background-color: black;
  img{
    height: 100%;
    margin-left: 20px;
  }
}
</style>
