<template>
    <header>
        <label>
            Name:
            <input type="text" placeholder="Pokemon Name" v-model="filter.name">
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

        <fieldset>
            <legend>
                Attack
            </legend>
                <label>
                    Min:
                    <input type="number" step="10" placeholder="0" v-model="filter.minAttack">
                </label>
                <label>
                    Max:
                    <input type="number" step="10" placeholder="0" v-model="filter.maxAttack">
                </label>
        </fieldset>
        
        <fieldset>
            <legend>
                Defense
            </legend>
                <label>
                    Min:
                    <input type="number" step="10" placeholder="0" v-model="filter.minDefense">
                </label>
                <label>
                    Max:
                    <input type="number" step="10" placeholder="0" v-model="filter.maxDefense">
                </label>
        </fieldset>

        <label>
            Sort By:
            <select v-model="sort.field">
                <optgroup label="Select Stat">
                    <option value="attack">Attack</option>
                    <option value="defense">Defense</option>
                </optgroup>
            </select>

            <select v-model="sort.direction">
                <optgroup label="Select Direction">
                    <option value="1">Ascending</option>
                    <option value="-1">Descending</option>
                </optgroup>
            </select>
        </label>
    </header>
</template>

<script>
export default {
  props: {
    filter: Object,
    types: Array,
    sort: Object
  }
};
</script>

<style scoped>
header {
    background:-webkit-linear-gradient(bottom, rgb(0, 0, 0), rgb(255, 0, 0));
    color: white;
    padding: 10px;
    text-align: center;
    border-radius: 20px;
}
</style>