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
            store,
            myOption: 'alien',
        }
    },
    created(){
        this.chiamataApiAlien()
    },
    methods: {
        chiamataApiAlien(){
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php${this.mySelection(this.myOption)}`)
            .then( res =>{
                const datiApi = res.data.data
                this.store.arrayCard = datiApi
            })
        },

        mySelection(myO){
            if (myO == 'alien') {
                return '?archetype=Alien'
            } else if(myO == 'photon'){
                return '?archetype=Photon'
            } else if(myO == 'branded'){
                return '?archetype=Branded';
            }
        }
    }
    
}
</script>

<template>
    <header>
        <HeaderComp/>
    </header>
    <main>
        <select v-model="myOption" @click="chiamataApiAlien">
            <option value="alien">Alien</option>
            <option value="photon">Photon</option>
            <option value="branded">Branded</option>
        </select>
        <MainComp/>
    </main>
</template>

<style lang="scss">
@use './style/main.scss';

main{
    background-color: #d48f38;
    padding: 4rem;

    select{
        padding: 8px 15px;
        border-radius: 5px;
        border: none;
        margin-bottom: 1rem;
    }
}
</style>
