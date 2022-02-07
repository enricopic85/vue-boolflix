<template>
    <div>
        <h2>FILM</h2>
        <div class="container" >
            <div class="card" v-for="film in films" :key="film.id" >
                <div class="img" >
                    <img v-if="film.poster_path===null" src="data:image/png;base64,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" alt="">
                    <img v-else :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
                </div>
                <div class="info">
                    <p>Titolo: {{film.title}}</p>
                    <p>Titolo originale: {{film.original_title}}</p>
                    <span>Voto:</span>
                    <i v-for="i in vote(film.vote_average)" :key="i" class="far fa-star"></i>
                    <div class="flags">
                        <p>Lingua:</p>
                        <div class="img-flag">
                            <img :src="`/flags/${film.original_language}.jpg`" alt="">
                        </div>
                    </div>
                    <p>Overwiew: {{film.overview}}</p>
                    <p>{{actor(film.id)}}</p>
                </div>
            </div> 
       </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            api_key: '41fa5602201a40cb6b8e1b749664bd8a',
            actors:[]
        }
    },
    mounted(){
        this.actor();
    },
    props:{
        films:Array
    },
     methods:{
        vote(voto){
            const results=Math.round(voto/2);
            return results;
        },
        actor(film_id){
             const params={
            api_key: this.api_key,
      }
       axios.get(`hhttps://api.themoviedb.org/3/movie/${film_id}/credits`,{params}).then((response)=>{
        this.actors= response.data.cast
    })
        }
    }
}
</script>

<style lang="scss" scoped>
@import './style/scrollbar.scss';
@import './style/card.scss';
</style>