<template>
    <header>
        <label>
            Name:
            <input type="text" v-model="filter.name">
        </label>
        <label>
            Type:
            <select v-model="filter.type">
                <option value="">All</option>
                <option
                    v-for="type in types"
                    v-bind:key="type"
                    v-bind:value="type">
                    {{type}}
                </option>
            </select>
        </label>
    </header>
</template>

<script>
export default {
  props: {
    filter: Object,
    types: Array
  }
};
</script>

<style scoped>
header {
    background:-webkit-linear-gradient(bottom, rgb(0, 0, 0), rgb(255, 0, 0));
    color: white;
    padding: 10px;
}
</style>