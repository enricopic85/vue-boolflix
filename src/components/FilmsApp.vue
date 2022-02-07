<template>
    <div>
        <h2>FILM</h2>
        <div class="container" >
            <my-films 
            :film="film"
            v-for="film in films" :key="film.id"/>
       </div>
    </div>
</template>

<script>
import axios from 'axios'
import MyFilms from './MyFilms.vue';
export default {
  components: { MyFilms },
    data(){
        return{
            api_key: '41fa5602201a40cb6b8e1b749664bd8a',
            actors:[]
        }
    },
    mounted(){
        this.actor(this.film.id);
    },
    props:{
        films:Array
    },
     methods:{
       
        actor(film_id){
             const params={
            api_key: this.api_key,
      }
       axios.get(`hhttps://api.themoviedb.org/3/movie/${film_id}/credits`,{params}).then((response)=>{
        this.actors= response.data.cast
    })
            console.log(this.actors)
        }
    }
}
</script>

<style lang="scss" scoped>
@import './style/scrollbar.scss';
@import './style/card.scss';
</style>