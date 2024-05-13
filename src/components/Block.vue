<template>
  <div class="block" v-if="showBlock" @click="stopTimer" :style="{ top: randomPosition(), left: randomPosition() }">
    click me
  </div>
</template>
<script>
export default {
 props: ['delay'],
 data() {
  return {
    showBlock: false,
    timer: null,
    reactionTime: 0
  }
 },
 mounted() {
  console.log('is mounted');
  setTimeout(() => {
    this.showBlock = true;
    this.startTimer();
    // console.log(this.delay);
  }, this.delay);
 },
 updated(){
  console.log('component uptdated')
 },
 unmounted() {
  console.log("unmounted")
 },
 methods: {
  startTimer() { 
    this.timer = setInterval(()=>{
      this.reactionTime += 10;
    }, 10);
  },
  stopTimer() { 
    clearInterval(this.timer);
    console.log(this.reactionTime);
    this.$emit('end', this.reactionTime);
  },
  randomPosition() {
      return Math.random() * (window.innerWidth - 400) + 'px';
    }
 }
}
</script>
<style>
  .block {
    position:absolute;
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>