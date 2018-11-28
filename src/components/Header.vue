<template>
    <header>
        <label>Attack:</label>
        <input type="number"
            v-model.number="filter.attack"
            step="50">

        <label>Attack:</label>
        <select v-model="filter.type">
            <option value="">All</option>
            <option
                v-for="type in types"
                v-bind:key="type"
                v-bind:value="type">
                {{type}}
            </option>
        </select>
    </header>
</template>

<script>
export default {
    props: {
        filter: Object,
    }
};
</script>

<style scoped>
header {
    background: steelblue;
    color: white;
    padding: 10px;
}
</style>
