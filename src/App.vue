<template>
 <h1>Bruce's Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue' /** remember, we have to import to main or root component */
import Results from './components/Results.vue' /** ditto */
export default {
  name: 'App',
  components: { Block, Results }, //? Gotta export the components to main.js which is then mounted to index.html */
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true 
      this.showResults = false   
    },
    endGame(reactionTime){
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
  color: white;
  border: none;
  padding: 8px 16 px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 1px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed
}
</style>
