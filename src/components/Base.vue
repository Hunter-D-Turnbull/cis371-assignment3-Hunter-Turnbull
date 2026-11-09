<template>
  <div
    class="baseBeverage"
    :style="{
      backgroundColor: color,
      height: height + '%'
    }"
  ></div>
</template>

<script setup lang="ts">
defineProps<{
  color: string;
  height: number;
}>();
</script>

<style scoped>
.baseBeverage {
  position: absolute;
  bottom: 0;
  left: 0;

  width: 100%;

  border-radius: 0 0 2.2em 2.2em;

  z-index: 1;

  animation: pour-tea 2s forwards;
}
</style>
