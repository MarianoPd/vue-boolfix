<template>
  <div class="my-card col-2">
    <ul >
        
        <li><strong>Title:</strong> {{title}}</li>
        <li><strong>Original Title:</strong> {{originalTitle}}</li>
        <li>
            <img v-if="checkFlagPresence()"  :src="require('../assets/img/'+ sendResult.original_language +'.png')" alt="">
            <strong v-else>{{sendResult.original_language}}</strong>
        </li>
        <li><strong>Vote:</strong> {{sendResult.vote_average}}</li>
        <img v-if="sendResult.poster_path !== null" :src="imgBaseUrl + sendResult.poster_path" alt="">
        
    </ul>
    
  </div>
</template>

<script>

export default {
    name: 'Card',
    data(){
        return{
            imgBaseUrl: 'https://image.tmdb.org/t/p/w342',
            title:'',
            originalTitle: '',
            language: '',
        }
    },
    props:{
        sendResult: Object,
        type: String,
    },
    
    methods:{
        checkFlagPresence(){
            if(this.sendResult.original_language === 'it') return true;
            if(this.sendResult.original_language === 'en') return true;
            return false;
        },
        fixProperties(){
            console.log('watch success');
            if(this.type === 'movie'){
                this.title = this.sendResult.title;
                this.originalTitle = this.sendResult.original_title;
                this.language = this.sendResult.original_language;
            }else if(this.type === 'serie'){
                this.title = this.sendResult.name;
                this.originalTitle = this.sendResult.original_name;
                this.language = this.sendResult.original_language;
            }
            console.log('watch success');
        }
    },
    mounted(){
        this.fixProperties();
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
            img{
                max-width: 100%;
            }
        }

    }
</style>