<template>
      <div class="result">
            <p>
                  Reaction Time : <strong> {{ score }} </strong> MS
            </p>
            <p class="rank">{{ rank }}</p>
      </div>
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
                  this.rank = "Excellent";
            } else if (this.score < 400) {
                  this.rank = "Good shot";
            } else {
                  this.rank = "snail pace...";
            }
      },
};
</script>

<style>
.rank {
      font-size: 1.3rem;
      color: #0faf87;
      font-weight: bold;
      padding: 15px 0;
}
</style>
