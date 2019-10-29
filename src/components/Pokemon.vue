<template>
    <div>
        <transition name="fade">
            <Modal
                v-if="show"
                :onClose="onClose"
                :pokemon="pokemon" />
        </transition>

        <li @click="handleClick" :style="{ background: pokemon.color_1 }">
            <img v-bind:src="pokemon.url_image"/>
            <h3> {{pokemon.pokemon}}</h3>
            <p>Type: {{pokemon.type_1}}, {{pokemon.type_2}}</p>
        </li>
    </div>
</template>

<script>
import Modal from './Modal';

export default {
  data() {
    return {
      show: false
    };
  },
  props: {
    pokemon: Object
  },
  methods: {
    handleClick() {
      this.show = true;
    },
    onClose() {
      this.show = false;
    }
  },
  components: {
    Modal
  }
};
</script>

<style>
li {
    border: 5px outset red;
    border-radius: 20px;
    margin: 20px auto;
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

.fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
}

.fade-enter, .fade-leave-to{
    opacity: 0;
}
</style>