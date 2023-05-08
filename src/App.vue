<script>
import axios from 'axios';
import {store} from './store';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import SelectMainComp from './components/SelectMainComp.vue';

export default{
    name:'App',
    components: {
    HeaderComp,
    MainComp,
    SelectMainComp,
    },
    data(){
        return{
            store,
        }
    },
    created(){
        this.chiamataApi
        this.archetypeCall()
    },
    computed: {
        chiamataApi(){
            if(store.myOption !== ''){

                axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${store.myOption}`)
                .then( res =>{
                    const datiApi = res.data.data
                    store.arrayCard = datiApi
                })
            } else {

            }
        },
    },
    methods: {
        archetypeCall(){
            axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                .then( (res) =>{
                this.store.archetypeArray = res.data
            })
        },
    },
}
</script>

<template>
    <header>
        <HeaderComp/>
    </header>
    <main>
        <SelectMainComp @nomeEmit="chiamataApi"/>
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
