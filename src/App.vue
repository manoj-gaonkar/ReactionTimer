<template>
  <h1>Reaction Timer</h1>
  <button @click="gameplay" :disabled="isPlaying" >Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endgame" />
  <Results v-if="showScore" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,
    };
  },
  components: { Block, Results },
  methods: {
    gameplay() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 4000;
      this.showScore = false;
      console.log(this.delay);
    },
    endgame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showScore = true;
    },
  },
};
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

button[disabled]{
  opacity: .3;
  cursor: not-allowed;
}
</style>