<template>
  <div class="my-card col-2">
    <ul v-if="type === 'movie'">
        <li><strong>Title:</strong> {{sendResult.title}}</li>
        <li><strong>Original Title:</strong> {{sendResult.original_title}}</li>
        <li>
            <img v-if="checkFlagPresence()"  :src="require('../assets/img/'+ sendResult.original_language +'.png')" alt="">
            <strong v-else>{{sendResult.original_language}}</strong>
        </li>
        <li><strong>Vote:</strong> {{sendResult.vote_average}}</li>
        
    </ul>
    <ul v-if="type === 'serie'">
        <li><strong>Title:</strong> {{sendResult.name}}</li>
        <li><strong>Original Title:</strong> {{sendResult.original_name}}</li>
        <li>
            <img v-if="checkFlagPresence()"  :src="require('../assets/img/'+ sendResult.original_language +'.png')" alt="">
            <strong v-else>{{sendResult.original_language}}</strong>
        </li>
        <li><strong>Vote:</strong> {{sendResult.vote_average}}</li>
        
    </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    data(){
        return{

        }
    },
    props:{
        sendResult: Object,
        type: String,
    },
    computed:{
        
    },
    methods:{
        checkFlagPresence(){
            if(this.sendResult.original_language === 'it') return true;
            if(this.sendResult.original_language === 'en') return true;
            return false;
        }
    },
}    
</script>

<style scoped lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';

    .my-card{
        background-color: cadetblue;
        color: white;
        border: 5px solid black;
        
        ul{
            list-style: none;
            li{

                img{
                    width: 50px;
                }
            }
        }

    }
</style>