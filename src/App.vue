<template>
  <h1>Reaction Timer</h1>
  <!-- disabled used to can't click button -->
  <button @click="startPlaying" :disabled="isPlaying">Play</button>
  <!-- v-bind blockDelay using the value of delay -->
  <Block v-if="isPlaying" :blockDelay="delay"/>
</template>

<script>
import Block from './components/Block.vue';

export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay : null,
    }
  },
  methods: {
    startPlaying(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
