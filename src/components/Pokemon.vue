<template>
    <li>
        <img style="height: 150px" v-bind:src="pokemon.url_image"/>
        <h3> {{pokemon.pokemon}} </h3>
        <p>Type: {{pokemon.type_1}}, {{pokemon.type_2}} </p>
        <p>Attack: {{ pokemon.attack }} </p>
        <p>Attack: {{ pokemon.attack }} </p>
    </li>
</template>

<script>
export default {
  props: {
    pokemon: Object
  }
};
</script>

<style>
li {
    border: 3px solid red;
    margin: 10px auto;
    padding: 0 30px;
    text-align: center;
}

img {
    border: 2px dashed goldenrod;
}

h3 {
    border: 2px solid gray;
}

p {
    margin: 10px;
    background: lightgray;
    font-weight: bold;
}
</style>