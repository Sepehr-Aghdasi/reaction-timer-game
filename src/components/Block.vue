<template>
      <div class="block" v-if="showBlock" @click="stopTimer()">
            <p>click</p>
      </div>
</template>

<script>
export default {
      props: ["delay"],
      data() {
            return {
                  showBlock: false,
                  timer: null,
                  reactionTimer: 0,
            };
      },
      mounted() {
            console.log("component mounted");
            setTimeout(() => {
                  this.showBlock = true;
                  this.startTimer();
                  // console.log(this.delay);
            }, this.delay);
      },
      updated() {
            console.log("component updated");
      },
      methods: {
            startTimer() {
                  this.timer = setInterval(() => {
                        this.reactionTimer += 10;
                  }, 10);
            },
            stopTimer() {
                  clearInterval(this.timer);
                  this.$emit("end", this.reactionTimer);
            },
      },
};
</script>

<style>
.block {
      width: 400px;
      border-radius: 20px;
      background-color: #0faf87;
      color: #fff;
      text-align: center;
      padding: 100px 0;
      margin: 50px auto;
      font-size: 2rem;
}
</style>
