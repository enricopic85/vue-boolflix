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

import MyFilms from './MyFilms.vue';
export default {
  components: { MyFilms },
    
   
    props:{
        films:Array
    },
     
}
</script>

<style lang="scss" scoped>
@import './style/scrollbar.scss';
@import './style/card.scss';
</style>