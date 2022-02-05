<template>
  <div id="app">
   <search-bar 
   @change="filterAll"
   />
   <main-app 
   :films="films"
   :series="series"
   />
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
      films:[],
      series:[],
      api_key: '41fa5602201a40cb6b8e1b749664bd8a',
      language:'it'
    }
  },
  mounted(){
     
  },

  methods:{
    
    filterFilms(input){
      const params={
        query:input,
        api_key: this.api_key,
        language:this.language
      }
      axios.get(`https://api.themoviedb.org/3/search/movie`, {params}).then((response)=>{
        this.films=response.data.results
    })
     
    },
     filterSeries(input){
        const params={
        query:input,
        api_key: this.api_key,
        language:this.language
      }
      axios.get(`https://api.themoviedb.org/3/search/tv`, {params}).then((response)=>{
        this.series=response.data.results
    })
    },
     filterAll(search){
      this.filterFilms(search)
      this.filterSeries(search)
    },
    
  }
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
