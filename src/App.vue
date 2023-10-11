<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  data() {
    return {
      delay: null,
      ispaly: false,
      score: null,
      showResult: false,
    };
  },
  methods: {
    play() {
      this.delay = 2000 + Math.random() * 5000;
      this.ispaly = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.ispaly = false;
      this.showResult = true;
    },
  },
  components: { Block, Result },
};
</script>


<template>
  <h1 class="headTitle">Reaction Timer</h1>
  <button class="playBtn" :disabled="ispaly" @click="play">Play</button>
  <!-- <p class="result" v-if="showResult">Reaction:{{ score }} ms</p> -->
  <Block v-if="ispaly" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<style >
.headTitle {
  text-align: center;
  display: flex;
  justify-content: center;
}
.playBtn {
  margin: 50px 10px;
  background-color: rgb(0, 171, 37);
  font-size: 24px;
  height: 50px;
  border-radius: 20px;
}
.result {
  font-size: 20px;
}
</style>
