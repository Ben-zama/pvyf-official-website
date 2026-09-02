<template>
  <div :class="['toggle', { 'is-active': isOpen }]">
    <div class="bars" id="bar1"></div>
    <div class="bars" id="bar2"></div>
    <div class="bars" id="bar3"></div>
  </div>
</template>

<script setup>
defineProps({
  isOpen: Boolean
});
</script>

<style lang="scss" scoped>
  .toggle {
    position: relative;
    width: 24px;
    height: 24px;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 6px;
    transition-duration: .5s;
  }

  .bars {
    width: 100%;
    height: 2px;
    background-color: $text-color;
    border-radius: 4px;
    transition-duration: .5s;
  }

  #bar2 {
    transition-duration: .5s;
  }

  #bar1,#bar3 {
    width: 70%;
  }

  .is-active .bars {
    position: absolute;
    background-color: red;
  }

  .is-active #bar2 {
    transform: scaleX(0);
  }

  .is-active #bar1 {
    transform: rotate(45deg);
    width: 100%;
  }

  .is-active #bar3 {
    transform: rotate(-45deg);
    width: 100%;
  }

  .is-active {
    transform: rotate(180deg);
  }
</style>
