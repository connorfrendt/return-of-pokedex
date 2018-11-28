<template>
    <ul>
        <Pokedex v-for="pokemon in pokedex"
            v-bind:key="pokemon.name"
            v-bind:pokemon="pokemon"/>
    </ul>
</template>

<script>
import Pokedex from './Pokemon.vue';

export default {
    props: {
        pokedex: Array
    },
    components: {
        Pokedex
    }
};
</script>

<style>

</style>
