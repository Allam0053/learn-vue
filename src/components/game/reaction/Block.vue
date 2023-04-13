<script lang="ts">
interface StateType {
  showBlock: boolean
  timer: NodeJS.Timeout | undefined
  reactionTime: 0
}
export default {
  props: ['delay'],
  emits: ['end'],
  data() {
    return {
      showBlock: false,
      timer: undefined,
      reactionTime: 0,
    } as StateType
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      // start the timer, tick every 10ms
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      // stop the timer
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    },
  },
}
</script>

<template>
  <div v-show="showBlock" class="block" @click="stopTimer">
    click me
  </div>
</template>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>
