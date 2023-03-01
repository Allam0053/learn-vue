<!-- eslint-disable no-console -->
<script setup>
import { ref } from 'vue'

const count = ref(0)
const mouseInDiv = ref(false)
const mousePosition = ref({ x: 0, y: 0 })

const notifyMouseInDiv = () => {
  console.log('Mouse in div', mouseInDiv.value, 'pos: ', mousePosition.value)
}

const notifyMouseOutFromDiv = () => {
  console.log('Mouse out from div', mouseInDiv.value, 'pos: ', mousePosition.value)
}

const handleMouseOver = (event) => {
  mousePosition.value = { x: event.offsetX, y: event.offsetY }
}

onMounted(() => {
  const element = document.querySelector('.my-element')
  element.addEventListener('mousemove', handleMouseOver)
})

onUnmounted(() => {
  const element = document.querySelector('.my-element')
  element.removeEventListener('mousemove', handleMouseOver)
})
</script>

<template>
  <div class="flex flex-col items-center">
    <button class="gray rounded-lg px-2 py-1" @click="() => count++">
      I Clicked {{ count }} times
    </button>
    <div ref="element" :class="{ gray: mouseInDiv }" class="my-element w-[800px] h-[800px]" @mouseenter="() => mouseInDiv = true" @mouseleave="() => mouseInDiv = false">
      <p>
        Mouse position: {{ mousePosition.x }}, {{ mousePosition.y }}
      </p>
      <div>
        <button class="bg-amber-500" @click="notifyMouseInDiv">
          Notify Mouse in Div
        </button>
      </div>
    </div>
    <div>
      <button @click="notifyMouseOutFromDiv">
        Notify Mouse out from Div
      </button>
    </div>
  </div>
</template>
