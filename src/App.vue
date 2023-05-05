<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import {store} from './store'

export default{
    name:'App',
    components: {
        HeaderComp,
    },
    data(){
        return{
            store
        }
    },
    created(){
        this.chiamataApi()
    },
    methods: {
        chiamataApi(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Alien')
            .then( res =>{
                const datiApi = res.data
                this.store.arrayCard = datiApi
            })
        }
    }
    
}
</script>

<template>
    <header>

    </header>
</template>

<style lang="scss">
@use './style/main.scss';
</style>
