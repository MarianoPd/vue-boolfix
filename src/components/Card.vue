<template>
  <div class="my-card col-2">
      <ul>
          <li><strong>Title:</strong> {{sendResult.title}}</li>
          <li><strong>Original Title:</strong> {{sendResult.original_title}}</li>
          <li><strong>Language:</strong> {{sendResult.original_language}}</li>
          <li><strong>Vote:</strong> {{sendResult.vote_average}}</li>
          
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        sendResult: Object,
    },
    computed:{
        
    }
}    
</script>

<style scoped lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';

    .my-card{
        background-color: cadetblue;
        color: white;
        padding: 20px;
        margin: 10px;
        ul{
            list-style: none;
        }
    }
</style>