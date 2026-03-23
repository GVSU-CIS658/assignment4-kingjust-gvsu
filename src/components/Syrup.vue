<template>
  <div
    v-if="currentSyrup.id !== 's1'"
    class="syrup"
    :style="{ backgroundColor: currentSyrup.color }"
  ></div>
</template>

<script setup lang="ts">
import { currentSyrup } from "../stores/beverage";
</script>
<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  opacity: 0;
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 1s 1s forwards;
  z-index: 2;
}

@keyframes pour-tea {
  0% {
    opacity: 1;
    transform: translateY(100%);
  }
  100% {
    opacity: 1;
    transform: translateY(0%);
  }
}
</style>
