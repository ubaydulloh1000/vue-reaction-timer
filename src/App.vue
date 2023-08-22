<template>

<div class="board">
  <h1>Reaction Timer game</h1>
  <ClickButton title="start game" v-if="!isPlaying" v-on:click="startGame" />
  <ClickButton title="end game" v-if="isPlaying" v-on:click="quitGame" />
  <GameBlock v-if="isPlaying" :delay="delay" @endGame="endGame"/>

  <ResultsBlock v-if="showResult" :score="reactionTime" />
  
  <div class="quit-message" v-if="showQuitMessage">
    <h3>you have quitted game. press start game to play again.</h3>
  </div>

</div>

</template>

<script>
import GameBlock from './components/Block.vue'
import ClickButton from './components/Button.vue'
import ResultsBlock from './components/Results.vue'

export default {
  name: 'App',
  components: {
    GameBlock,
    ClickButton,
    ResultsBlock,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
      showResult: false,
      showQuitMessage: false
    }
  },
  methods: {
    startGame() {
      this.isPlaying = true
      this.showResult = false
      this.showQuitMessage = false
      this.delay = 2000 + Math.random() * 5000
    },
    endGame(reactionTime){
      this.isPlaying = false
      this.reactionTime = reactionTime
      this.showResult = true
    },
    quitGame(){
      this.isPlaying = false
      this.showResult = false
      this.showQuitMessage = true
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

.board{
  width: 100%;
  height: 100%;
}
</style>
