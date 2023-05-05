<script>
import axios from 'axios';
import {store} from './store';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

export default{
    name:'App',
    components: {
        HeaderComp,
        MainComp,
    },
    data(){
        return{
            store
        }
    },
    created(){
        this.chiamataApiAlien()
    },
    methods: {
        chiamataApiAlien(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Alien')
            .then( res =>{
                const datiApi = res.data.data
                this.store.arrayCard = datiApi
                console.log(datiApi)
            })
        }
    }
    
}
</script>

<template>
    <header>
        <HeaderComp/>
    </header>
    <main>
        <MainComp/>
    </main>
</template>

<style lang="scss">
@use './style/main.scss';

main{
    background-color: #d48f38;
    padding: 4rem;
}
</style>
