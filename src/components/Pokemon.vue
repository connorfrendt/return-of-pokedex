<template>
    <li>
        <div class="info">
            <h3> {{ pokemon.pokemon }} </h3>
            <p> {{ pokemon.attack }} </p>
            <p> {{ pokemon.defense }} </p>
        </div>
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
    list-style: none;
}

p {
    display: inline;
}
</style>