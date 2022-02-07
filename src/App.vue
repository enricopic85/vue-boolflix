<template>
  <div id="app">
   <search-bar 
   @searchGenre="genreFilterAll"
   @change="filterAll"
   :genre="genre"
   />
   <main-app 
   :films="genreFilms"
   :series="genreSeries"
   :trend="filteredTrend"
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
      trend:[],
      filteredTrend:[],
      genreFilms:[],
      genreSeries:[],
      api_key: '41fa5602201a40cb6b8e1b749664bd8a',
      language:'it',
      genre:[],
    }
  },
  mounted(){
        this.trends();
        this.genreList();
  },

  methods:{
    genreFilterAll(genre_id){
        this.filterTrend(genre_id);
        this.filtersFilms(genre_id);
        this.filtersSeries(genre_id)
    },
    filterTrend(genre_id){
        this.filteredTrend=this.trend.filter((movie)=>{
          return movie.genre_ids.includes(genre_id) || genre_id === 'all'
        })
    },
    filtersFilms(genre_id){
        this.genreFilms= this.films.filter((movie)=>{
          return movie.genre_ids.includes(genre_id) || genre_id === 'all'
        })
    },
    filtersSeries(genre_id){
        this.genreSeries= this.series.filter((movie)=>{
          return movie.genre_ids.includes(genre_id) || genre_id === 'all'
        })
    },
    genreList(){
         const params={
        api_key: this.api_key,
      }
       axios.get(`https://api.themoviedb.org/3/genre/movie/list`, {params}).then((response)=>{
        this.genre= response.data.genres
    })
    },

    trends(){
      const params={
        api_key: this.api_key,
      }
        axios.get(`https://api.themoviedb.org/3/trending/movie/week`, {params}).then((response)=>{
        this.trend = response.data.results
        this.filteredTrend = response.data.results
    })
    
        
    },
    async  filterFilms(input){
      this.films= await this.callApi(input,'movie');
      this.genreFilms= await this.callApi(input,'movie');
    },
    
    async filterSeries(input){
      this.series= await this.callApi(input,'tv');
      this.filteredSeries= await this.callApi(input,'tv')
    },

   async callApi(input,type){
       const params={
        query:input,
        api_key: this.api_key,
        language:this.language
      }
      const results= await axios.get(`https://api.themoviedb.org/3/search/${type}`, {params}).then((response)=>{
        return response.data.results
    })
      return results;
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
