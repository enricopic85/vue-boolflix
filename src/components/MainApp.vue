<template>
    <div class="container-card">
        <trends-app :trend="trend" v-if="(films.length===0 && series.length===0) "/>
        <films-app :films="films" v-if="films.length>0"/>
        <series-app :series="series" v-if="series.length>0"/>
    </div>
</template>

<script>
import FilmsApp from './FilmsApp.vue'
import SeriesApp from './SeriesApp.vue'
import TrendsApp from './TrendsApp.vue'
export default {
    
    components:{
        FilmsApp,
        SeriesApp,
        TrendsApp
    },
    props:{
        films:Array,
        series:Array,
        trend:Array
    },
}
</script>

<style lang="scss" scoped>
   
</style>