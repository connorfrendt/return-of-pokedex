<template>
    <li :style="{ background: pokemon.color_1 }">
        <img v-bind:src="pokemon.url_image"/>
        <h3> {{pokemon.pokemon}}</h3>
        <p>Type: {{pokemon.type_1}}, {{pokemon.type_2}}</p>
        <p>Attack: {{pokemon.attack}}</p>
        <p>Defense: {{pokemon.defense}}</p>
        <p>Special Attack: {{pokemon.special_attack}}</p>
        <p>Special Defense: {{pokemon.special_defense}}</p>
        <p>Speed: {{pokemon.speed}}</p>
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
    border: 5px outset red;
    border-radius: 20px;
    margin: 10px auto;
    padding: 0 30px;
    text-align: center;
    box-shadow: 6px 6px 6px black;
}

img {
    height: 150px;
}

h3 {
    border: 5px outset gray;
    background: white;
    color: black
}

p {
    margin: 10px;
    background: lightgray;
    font-weight: bold;
    border-radius: 10px;
    padding: 5px;
}
</style>
