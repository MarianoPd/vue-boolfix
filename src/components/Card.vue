<template>
  <div class="my-card col-2">
    <ul >        
        <li><strong>Title:</strong> {{title}}</li>
        <li><strong>Original Title:</strong> {{originalTitle}}</li>
        <li>
            <img v-if="checkFlagPresence()"  :src="flag" alt="language">
            <strong v-else>{{language}}</strong>
        </li>
              
    </ul>
    <div class="vote">
            <i v-if="(vote > 0)" class="fas fa-star gold"></i>
            <i v-else class="fas fa-star gray"></i>
            <i v-if="(vote > 1)" class="fas fa-star gold"></i>
            <i v-else class="fas fa-star gray"></i>
            <i v-if="(vote > 2)" class="fas fa-star gold"></i>
            <i v-else class="fas fa-star gray"></i>
            <i v-if="(vote > 3)" class="fas fa-star gold"></i>
            <i v-else class="fas fa-star gray"></i>
            <i v-if="(vote > 4)" class="fas fa-star gold"></i>
            <i v-else class="fas fa-star gray"></i>
            
    </div>
    <h1>{{vote}}</h1>
    <img v-if="sendResult.poster_path !== null" :src="imgBaseUrl + sendResult.poster_path" alt="">

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
            flag: '',
            vote: 0,
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
            
            if(this.type === 'movie'){
                this.title = this.sendResult.title;
                this.originalTitle = this.sendResult.original_title;
            }else if(this.type === 'serie'){
                this.title = this.sendResult.name;
                this.originalTitle = this.sendResult.original_name;
            }
            this.language = this.sendResult.original_language;
            this.vote = Math.ceil(this.sendResult.vote_average /2);
            if(this.checkFlagPresence()){
                this.flag = require('../assets/img/'+ this.language +'.png');
            }            
                        
        }
    },
    mounted(){
        this.fixProperties();
        console.log('card mounted');
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
        img{
                max-width: 100%;
        }

        .vote{
            .gold{
                color: gold;
            }
            .gray{
                color: gray;
            }
        }

    }
</style>