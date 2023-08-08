<template>
  <h2>Kenzo Reaction Timer</h2>
  <button @click="start" :disabled="isPlaying" > Play</button>
  <Block v-if="isPlaying" :delay="delay"  @end="endGame"/>
  <Result  v-if="showResult" :score="score"/>
  
</template>

<script>
//v-if="showResult"
import Block from "./components/Block"
import Result from "./components/Result"

export default {
  name: 'App',
  components: {
   Block,
   Result
  },
  data() {
    return{
      isPlaying: false,
      showResult: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.showResult = false
      this.delay = 2000 + Math.random() * 5000
    },
    endGame (reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  color: #2c3e50;
  margin-top: 60px;
}
body{
  background: white;
}
button{
  color: white;
  background: #0faf87;
  border: none;
  padding: 8px 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  border-radius: 4px;
}
button[disabled]{
  opacity: .2;
  cursor: not-allowed;
}
</style>
