<template>
  <h1>Ninja reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play!</button>
  <Block_ v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Game_Results v-if="showResults" :score="score"/>
</template>

<script>
import Block_ from './components/Block_.vue'
import Game_Results from './components/Game_Results.vue'
export default {
  name: 'App',
  components: { Block_, Game_Results},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      console.log(this.delay)
      this.showResults = false
    },
    endGame(reactionTime) {
      // reactionTime passed as parameter with 'end' event from Block component
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf87;
  border: white;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0,2;
  cursor: not-allowed;
}
</style>
