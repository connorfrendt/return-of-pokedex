<template>
    <transition-group
      name="staggered-list-demo"
      tag="ul"
      v-bind:css="false"
      v-on:before-enter="beforeEnter"
      v-on:enter="enter"
      v-on:leave="leave"

    >
      <Pokemon v-for="pokemon in pokemons"
          v-bind:key="pokemon.pokemon"
          v-bind:pokemon="pokemon"
          class="list-complete-item"/>
    </transition-group>
</template>

<script>
import Pokemon from './Pokemon.vue';

export default {
  props: {
    pokemons: Array
  },
  components: {
    Pokemon
  },
  methods: {
    beforeEnter: function(el) {
      el.style.opacity = 0;
    },
    enter: function(el, done) {
      var vm = this;
      /* eslint-disable-next-line */
      Velocity(el,
        { opacity: 1 },
        {
          duration: this.fadeInDuration,
          complete: function() {
            done();
            if(!vm.stop) vm.show = false;
          }
        }
      );
    },
    leave: function(el, done) {
      var vm = this;
      /* eslint-disable-next-line */
      Velocity(el,
        { opacity: 0 },
        {
          duration: this.fadeOutDuration,
          complete: function() {
            done();
            vm.show = true;
          }
        }
      );
    }
  }
};
</script>

<style scoped>
ul {
  display: grid;
  grid-column-gap: 40px;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  list-style-type: none;
  margin: 0;
  padding: 0;
  }

.list-complete-item {
  transition: .5s;
  display: inline-block;
}

.list-complete-enter, .list-complete-leave-to {
  opacity: 0;
}

.list-complete-leave-active {
  position: absolute;
}
</style>
