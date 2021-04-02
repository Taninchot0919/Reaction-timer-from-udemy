<template>
  <h1>Reaction Timer</h1>
  <!-- disabled used to can't click button -->
  <button @click="startPlaying" :disabled="isPlaying">Play</button>
  <!-- v-bind blockDelay using the value of delay -->
  <Block v-if="isPlaying" :blockDelay="delay" @stopTimer="endGame"/>
  <Result v-if="showResult" :result="score" />
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay : null,
      score : null,
      showResult : false,
    }
  },
  methods: {
    startPlaying(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime){
      console.log('This method used from app.vue')
      console.log(reactionTime)
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
button{
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
