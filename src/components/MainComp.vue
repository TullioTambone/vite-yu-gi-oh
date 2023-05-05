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
        </div>
        <div class="row gap-1">
            <SingolaCarta v-for="(element, index) in store.arrayCard" :key="index" :nomeCard="element"/>
        </div>
    </div>
</template>

<style lang="scss" scoped>
#main-id{
    background-color: white;
    padding: 1.5rem;

    .banner-counter{
        background-color: #212529;
        padding: 1rem;
    }
    .row{
        justify-content: center;
    }
}
</style>