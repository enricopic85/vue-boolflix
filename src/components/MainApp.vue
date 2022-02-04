<template>
    <div class="container-card">
        <films-app :films="films"/>
        <series-app :series="series"/>
    </div>
</template>

<script>
import FilmsApp from './FilmsApp.vue'
import SeriesApp from './SeriesApp.vue'
export default {
    components:{
        FilmsApp,
        SeriesApp,
    },
    props:{
        films:Array,
        series:Array
    },
}
</script>

<style lang="scss" scoped>
</style>