<template>
  <p>Reaction time: {{ scoreProp }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['scoreProp'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja fingers'
    } else if (this.score < 600) {
      this.rank = "Rapid Reflexes"
    } else {
      this.rank = "Snail pace ..."
    }
  }
}
</script>

<style>
  .rank {
    font-size: 1.4 em;
    color: #0faf87;
    font-weight: bold;
  }
</style>