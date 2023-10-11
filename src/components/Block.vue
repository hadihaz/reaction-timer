<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Stop</div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      timer: null,
      reactiontimer: 0,
    };
  },
  props: ["delay"],
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactiontimer += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      //   console.log(this.reactiontimer);
      this.$emit("end", this.reactiontimer);
    },
  },
};
</script>

<style>
.block {
  width: 250;
  height: 200px;
  background-color: rgb(0, 171, 37);
  font-size: 20px;
  border-radius: 20px;
  margin-top: 20px;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>