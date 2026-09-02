<script setup>
import { ref } from 'vue'
import gsap from 'gsap'

const ripple1 = ref(null)
const ripple2 = ref(null)
const ripple3 = ref(null)
const ripple4 = ref(null)

const getScale = () => {
  const diag = Math.sqrt(window.innerWidth ** 2 + window.innerHeight ** 2)
  return diag / 20 // 40px base size -> 20px radius
}

const startTransition = (x, y) => {
  return new Promise(resolve => {
    gsap.set([ripple1.value, ripple2.value, ripple3.value, ripple4.value], {
      left: x,
      top: y,
      xPercent: -50,
      yPercent: -50,
      scale: 0
    })

    const tl = gsap.timeline({ onComplete: resolve })
    const scale = getScale()
    
    tl.to(ripple1.value, { scale: scale, duration: 0.6, ease: 'power2.inOut' })
      .to(ripple2.value, { scale: scale, duration: 0.6, ease: 'power2.inOut' }, "-=0.45")
      .to(ripple3.value, { scale: scale, duration: 0.6, ease: 'power2.inOut' }, "-=0.45")
      .to(ripple4.value, { scale: scale, duration: 0.6, ease: 'power2.inOut' }, "-=0.45")
  })
}

const finishTransition = () => {
  return new Promise(resolve => {
    gsap.set([ripple1.value, ripple2.value, ripple3.value, ripple4.value], { scale: 0 })
    resolve()
  })
}

defineExpose({
  startTransition,
  finishTransition
})
</script>

<template>
  <div class="page-transition-overlay">
    <div class="ripple ripple-1" ref="ripple1"></div>
    <div class="ripple ripple-2" ref="ripple2"></div>
    <div class="ripple ripple-3" ref="ripple3"></div>
    <div class="ripple ripple-4" ref="ripple4"></div>
  </div>
</template>

<style lang="scss" scoped>
.page-transition-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  z-index: 9999;
  overflow: hidden;

  .ripple {
    position: absolute;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    transform: translate(-50%, -50%) scale(0);
    will-change: transform;
    &.ripple-1 { background: $brand-color-1; }
    &.ripple-2 { background: $brand-color-2; }
    &.ripple-3 { background: $brand-color-3; }
    &.ripple-4 { background: $secondary-color; }
  }
}
</style>
