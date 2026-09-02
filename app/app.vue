<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useRouter } from 'vue-router'

const overlayRef = ref(null)
const router = useRouter()
let lastClick = { x: 0, y: 0 }

const updateClickPos = (e) => {
  lastClick = { x: e.clientX, y: e.clientY }
}

onMounted(() => {
  document.addEventListener('click', updateClickPos)
  lastClick = { x: window.innerWidth / 2, y: window.innerHeight / 2 }
})

onUnmounted(() => {
  document.removeEventListener('click', updateClickPos)
})

router.beforeResolve(async (to, from) => {
  if (to.path !== from.path) {
    if (overlayRef.value) {
      await overlayRef.value.startTransition(lastClick.x, lastClick.y)
    }
  }
})

router.afterEach(() => {
  setTimeout(() => {
    if (overlayRef.value) {
      overlayRef.value.finishTransition()
    }
  }, 50)
})
</script>

<template>
  <div>
    <NuxtLayout />
    <PageTransitionOverlay ref="overlayRef" />
  </div>
</template>