<template>
    <header>
        <label>Attack:</label>
        <input type="number"
            v-model.number="filter.attack"
            step="25">

        <label>Type:</label>
        <select v-model="filter.type_1">
            <option value="">All</option>
            <option
                v-for="type_1 in types"
                v-bind:key="type_1"
                v-bind:value="type_1">
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
