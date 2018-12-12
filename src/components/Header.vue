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

        <div id="stat-filter">
            <fieldset>
                <legend>
                    Attack
                </legend>
                    <label>
                        Min:
                        <input type="number" step="10" placeholder="0" v-model="filter.minAttack">
                    </label>
                        <br />
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
                        <br />
                    <label>
                        Max:
                        <input type="number" step="10" placeholder="0" v-model="filter.maxDefense">
                    </label>
                    <br />
            </fieldset>

            <fieldset>
                <legend>
                    Special Attack
                </legend>
                    <label>
                        Min:
                        <input type="number" step="10" placeholder="0" v-model="filter.minSpAtk">
                    </label>
                        <br />
                    <label>
                        Max:
                        <input type="number" step="10" placeholder="0" v-model="filter.maxSpAtk">
                    </label>
            </fieldset>

            <fieldset>
                <legend>
                    Special Defense
                </legend>
                    <label>
                        Min:
                        <input type="number" step="10" placeholder="0" v-model="filter.minSpDef">
                    </label>
                        <br />
                    <label>
                        Max:
                        <input type="number" step="10" placeholder="0" v-model="filter.maxSpDef">
                    </label>
            </fieldset>

            <fieldset>
                <legend>
                    Speed
                </legend>
                    <label>
                        Min:
                        <input type="number" step="10" placeholder="0" v-model="filter.minSpeed">
                    </label>
                        <br />
                    <label>
                        Max:
                        <input type="number" step="10" placeholder="0" v-model="filter.maxSpeed">
                    </label>
            </fieldset>
        </div>

        <label>
            Sort By:
            <select v-model="sort.field">
                <optgroup label="Select Stat">
                    <option value="none">None</option>
                    <option value="attack">Attack</option>
                    <option value="defense">Defense</option>
                    <option value="spAtk">Special Attack</option>
                    <option value="spDef">Special Defense</option>
                    <option value="speed">Speed</option>
                </optgroup>
            </select>

            <select v-model="sort.direction">
                <optgroup label="Select Direction">
                    <option value="0">None</option>
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

#stat-filter {
    display: flex;
    justify-content: center;
}
</style>