<template>
  <div
    v-if="currentCreamer.id !== 'c1'"
    class="froth"
    :style="{ backgroundColor: '#c6c6c6', animationDelay: animDelay }"
  >
    <div
      v-for="n in 5"
      :key="n"
      class="foam"
      :style="{ background: currentCreamer.color }"
    ></div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { currentCreamer, currentSyrup } from "../stores/beverage";

const hasSyrup = computed(() => currentSyrup.value.id !== "s1");
const animDelay = computed(() => (hasSyrup.value ? "2s" : "1s"));
</script>
<style lang="scss" scoped>
.froth {
  overflow: visible;
  transform: translateY(400%);
  opacity: 0;
  position: relative;
  height: 20%;
  width: 100%;
  animation: pour-tea 1s linear forwards;
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
.foam {
  display: block;
  border-radius: 30px;
  height: 40px;
  width: 40px;
  position: absolute;
}

.foam:nth-child(1) {
  top: 0px;
  left: -3px;
}

.foam:nth-child(2) {
  top: 0px;
  left: 55px;
}

.foam:nth-child(3) {
  width: 30px;
  height: 30px;
  border-radius: 40px;
  top: 3px;
  left: 30px;
}

.foam:nth-child(4) {
  width: 30px;
  height: 30px;
  border-radius: 45px;
  top: 5px;
  right: -2px;
}

.foam:nth-child(5) {
  top: 2px;
  right: 10px;
}
</style>
