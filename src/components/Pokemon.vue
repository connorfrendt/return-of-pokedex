<template>
    <ul>
        <img v-bind:src="pokemon.url_image"/>
        <h3> {{ pokemon.pokemon }} </h3>
        <p>Attack: {{ pokemon.attack }} </p>
        <p>Defense: {{ pokemon.defense }} </p>
    </ul>
</template>

<script>
export default {
  props: {
    pokemon: Object
  }
};
</script>

<style scoped>
ul {
    display: grid;
    grid-template-columns: repeat(autofit, minmax(200px, 1fr));
    list-style: none;
    margin: 0;
    padding: 0;
}
</style>