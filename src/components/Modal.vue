<template>
  <div class="modal" @click="onClose" @keyup.esc="onClose">
    <div class="content" @click.stop="">
      <button class="close" @click="onClose">X</button>
      <slot id="modal">
        <img v-bind:src="pokemon.url_image" style="height: 250px"/>
        <p>#{{pokemon.species_id}}</p>
        <p>Type: {{pokemon.type_1}}, {{pokemon.type_2}}</p>
        <p>HP: {{pokemon.hp}}</p>
        <p>Attack: {{pokemon.attack}}</p>
        <p>Defense: {{pokemon.defense}}</p>
        <p>Special Attack: {{pokemon.special_attack}}</p>
        <p>Special Defense: {{pokemon.special_defense}}</p>
        <p>Speed: {{pokemon.speed}}</p>
        <p>Abilities: {{pokemon.ability_1}}/{{pokemon.ability_2}}</p>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    onClose: Function,
    pokemon: Object
  },
  created() {
    console.log('Modal created');
    this.documentListener = event => {
      if(event.keyCode === 27) {
        console.log('closing');
        this.onClose();
      }
    };
    document.addEventListener('keyup', this.documentListener);
  },
  destroyed() {
    document.removeEventListener('keyup', this.documentListener);
  }
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0; left: 0;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, .5);
}

.content {
  position: relative;
  background:-webkit-radial-gradient(rgb(255, 255, 255), rgb(0, 0, 0));
  padding: 40px;
  border: 5px outset black;
  border-radius: 15px;
}

p {
  background: black;
  color: white;
  text-align: center;
}

.close {
  position: absolute;
  top: 5px;
  left: 5px;
  background: red;
  border-radius: 20px;
}
</style>