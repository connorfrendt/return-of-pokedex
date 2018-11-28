<template>
    <li>
        
        <div class="info">
            <h3> {{ pokemon.pokemon }} </h3>
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
</style>
