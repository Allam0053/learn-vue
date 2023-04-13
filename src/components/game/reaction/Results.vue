<script lang="ts">
interface StateType {
  rank?: string
}
export default {
  props: ['score'],
  data() {
    return {
      rank: undefined,
    } as StateType
  },
  mounted() {
    if (this.score < 250)
      this.rank = 'Ninja Fingers'
    else if (this.score < 400)
      this.rank = 'Rapid Reflexes'
    else
      this.rank = '...Snail Pace'
  },
}
</script>

<template>
  <p>Reaction time - {{ score }} ms</p>
  <p class="rank">
    {{ rank }}
  </p>
</template>

<style>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>
