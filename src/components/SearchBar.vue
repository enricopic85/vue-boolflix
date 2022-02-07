<template>
    <div class="search">
        <div class="logo">BOOLFLIX</div>
        <ul>
            <li v-for="(voice,i) in voicesMenu" :key="i">{{voice}}</li>
        </ul>
        <div class="input"><input type="text" v-model="search" @keyup.enter="resetInput()"></div>
        <i @click="resetInput()" class="fas fa-search"></i>
        <i class="fas fa-bell">
            <div class="counter">1</div>
        </i>
        <select name="genre" id="genre" v-model="searchGenre" @change="$emit('searchGenre',searchGenre)">
            <option value="all">all</option>
            <option v-for="gen in genre" :key="gen.id" :value=gen.id>{{gen.name}}</option>
        </select>
    </div>
</template>

<script>
export default {
    data(){
        return{
            search:'',
            searchGenre: '',
            voicesMenu:['Home','Serie Tv','Film','Original','Aggiunti di recente','La mia lista'],
            visible:false
        }
    },
    methods:{
        resetInput(){
            this.$emit('change',this.search)
            this.search=""
        },
        changeVisible(){
            this.visible=!this.visible
        }
    },
    props:{
        genre:Array
    }
}
</script>

<style lang="scss" scoped>
@import './style/main.scss';
    .search{
        width: 100%;
        height: 50px;
        color: red;
        background-color: black;
        display: flex;
        align-items: center;
        ul{
            display: flex;
            flex-grow: 1;
        }
        li{
            color: white;
            list-style: none;
            font-size: 11px;
            padding-right: 10px;
        }
        i{
            padding-right: 30px;
            cursor: pointer;
        }
        .fa-bell{
            color: white;
            position: relative;
            .counter{
                background-color: red;
                text-align: center;
                border-radius: 50%;
                position: absolute;
                top:-6px;
                left: 10px;
                width: 15px;
                height: 15px;
            }
        }
        #genre{
            margin-right: 30px;
        }
        .logo{
            // flex-grow: 1;
            padding-left: 16px;
            font-weight: 800px;
            padding-right: 30px;
            font-size: 18px;
             color: red;
        }
        .input{
            padding-right: 10px;
            border-radius: 5px;
        }
        .button{
            padding-right: 20px;
        }
    }
</style>