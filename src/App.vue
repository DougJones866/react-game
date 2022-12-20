<template>
 <h1>React Game</h1>
 <!-- <button @click="start" :disabled="isPlaying">Play</button> -->
 <h3>Choose A Game Setting</h3>
 <button @click="easyGame" :disabled="isPlaying" >Easy</button><button @click="hardGame" :disabled="isPlaying">Hard</button>
 <Block v-if="isPlaying" :delay="delay" :easy="easy" :hard="hard" @end="endGame"/>
 <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
   Block,
   Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      easy: false,
      hard: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    easyGame(){
      this.easy = true
      this.hard = false
      this.start()
      

    },
    hardGame(){
      this.hard = true
      this.easy = false
      this.start()
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.hard = false
      this.east = false
      this.showResults = true
    },
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
  color:white;
  border:none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
