<script lang="ts">
import { reactive } from 'vue'

export default {
  setup() {
    const myobj = reactive({ firstchild: { secondchild: 'something' } })

    const updateSecondChild = () => {
      myobj.firstchild.secondchild = 'something else'
    }

    return {
      myobj,
      updateSecondChild,
    }
  },
}
</script>

<template>
  <div>
    <p>First Child: {{ myobj.firstchild }}</p>
    <p>Second Child: {{ myobj.firstchild.secondchild }}</p>
    <button @click="updateSecondChild">
      Update Second Child
    </button>
  </div>
</template>
