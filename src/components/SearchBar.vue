<template>
    <div class="search">
        <div class="logo">BOOLFLIX</div>
        <div class="input"><input type="text" v-model="search"></div>
        <div class="button"><button @click="resetInput()">Search</button></div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            search:'',
        }
    },
    props:{
        visible:Boolean
    },
    methods:{
        resetInput(){
            this.$emit('change',this.search)
            this.search=""
        },
    }
}
</script>

<style lang="scss" scoped>
    .search{
        width: 100%;
        height: 50px;
        background-color: black;
        display: flex;
        color: red;
        align-items: center;
        .logo{
            flex-grow: 1;
            padding-left: 16px;
            font-weight: 800px;
        }
        .input{
            padding-right: 50px;
        }
        .button{
            padding-right: 20px;
        }
    }
</style>