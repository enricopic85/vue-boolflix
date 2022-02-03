<template>
    <div class="search">
        <div class="logo">BOOLFLIX</div>
        <div><input type="text" v-model="search"></div>
        <div><button @click="$emit('change',search)">Search</button></div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            search:''
        }
    }
}
</script>

<style lang="scss" scoped>
    .search{
        width: 100%;
        height: 100px;
        background-color: black;
        display: flex;
        color: red;
        align-items: center;
        .logo{
            flex-grow: 1;
        }
    }
</style>