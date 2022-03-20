<template>
      <div>
            <h1>Vue Reaction Timer</h1>
            <button class="playBtn" @click="start()" :disabled="isPlaying">play</button>
            <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
            <Result v-if="showResult" :score="score">Reaction Time : {{ score }} ms</Result>
      </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
      components: { Block, Result },
      name: "App",
      data() {
            return {
                  isPlaying: false,
                  showResult: false,
                  delay: null,
                  score: null,
            };
      },
      methods: {
            start() {
                  this.delay = 2000 + Math.random() * 5000;
                  this.isPlaying = true;
                  this.showResult = false;
                  // if (this.isPlaying == true) {
                  //       document.querySelector(".playBtn").classList.add("disabled");
                  // }
            },
            endGame(reactionTimer) {
                  this.score = reactionTimer;
                  this.isPlaying = false;
                  this.showResult = true;
            },
      },
};
</script>

<style>
* {
      margin: 0;
      padding: 0;
      border: none;
      outline: none;
      text-decoration: none;
      list-style-type: none;
      box-sizing: border-box;
}
#app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #444;
      margin-top: 60px;
}
.playBtn {
      padding: 0.575rem 1.175rem;
      border: none;
      outline: none;
      border-radius: 5px;
      font-size: 1rem;
      margin: 20px;
      background-color: #0faf87;
      color: #fff;
      font-weight: bold;
      transition: 0.3s;
}
.playBtn:hover {
      transition: 0.3s;
      transform: scale(1.2);
      cursor: pointer;
      box-shadow: rgba(0, 0, 0, 0.1) -4px 9px 25px -6px;
}
.playBtn[disabled] {
      opacity: 0.2;
      transform: scale(1) !important;
      cursor: not-allowed !important;
}
</style>
