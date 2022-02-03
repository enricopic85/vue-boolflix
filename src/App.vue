<template>
  <div id="app">
   <search-bar @change="filterFilms"/>
   <main-app :films="films"/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import MainApp from './components/MainApp.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    SearchBar,
    MainApp
  },
  data(){
    return{
      films:[]
    }
  },
  mounted(){
      
  },
  methods:{
    filterFilms(search){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=41fa5602201a40cb6b8e1b749664bd8a&language=it&query=${search}`).then((response)=>{
        this.films=response.data.results
    })
      return this.films
    }
  }
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
