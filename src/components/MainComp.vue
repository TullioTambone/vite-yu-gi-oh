<script>
import SingolaCarta from './SingolaCarta.vue';
import {store} from '../store';

export default{
    name:'MainComp',

    components: {
        SingolaCarta,
    },
    data(){
        return{
            store,
        }
    }
}
</script>

<template>
    <div id="main-id">
        <div class="banner-counter">
            <h5>Carte Trovate: {{ store.arrayCard.length }}</h5>
        </div>
        <div class="row gap-1">
            <SingolaCarta v-for="(element, index) in store.arrayCard" :key="index" :nomeCard="element"/>
        </div>
    </div>
</template>

<style lang="scss" scoped>
#main-id{
    background-color: white;
    padding: 1rem;
    .banner-counter{
        margin: 0 auto;
        width: 90%;
        background-color: #212529;
        color: white;
        padding: 0.5rem;
    }
    .row{
        margin-top: 0.5rem;
        justify-content: center;
    }
}
</style>