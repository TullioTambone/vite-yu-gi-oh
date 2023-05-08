<script>
import {store} from '../store';

export default{
    name:"SelectMainComp",
    data(){
        return{
            store,
        }
    }
}
</script>

<template>
    <select v-model="store.myOption" @click="$emit('nomeEmit')">
        <option disabled value="">Ricerca per Archetipo</option>
        <option :value="element.archetype_name" v-for="(element, index) in store.archetypeArray" :key="index" >{{ element.archetype_name }}</option>
    </select>
</template>

<style lang="scss" scoped>
    select{
        padding: 8px 15px;
        border-radius: 5px;
        border: none;
        margin-bottom: 1rem;
    }
</style>