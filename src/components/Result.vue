<template>
  <p class="result">Reaction:{{ score }} ms</p>
  <p class="result">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "good";
    } else if (this.score < 750) {
      this.rank = "nice";
    } else {
      this.rank = "bad";
    }
  },
};
</script>

<style>
.result {
  font-size: 20px;
}
</style>