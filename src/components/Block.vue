<template>
  <div class="container" v-if="showBlock" @click="stopTimer">
    <h3>Click here {{ delay }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
      console.log("mounted");
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      this.showBlock = false;
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
button {
  padding: 8px 20px;
  border: none;
  background: rgb(255, 240, 30);
  border-radius: 5px;
}

.container {
  width: 30%;
  background: rgb(135, 230, 155);
  margin: 100px auto;
  height: 300px;
  border-radius: 10px;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>