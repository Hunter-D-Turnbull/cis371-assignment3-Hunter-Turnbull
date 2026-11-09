<template>
  <div
    class="syrup"
    :style="{
      background: name === 'Vanilla'
        ? 'repeating-linear-gradient(45deg, white, white 10px, #e1cf95 10px, #e1cf95 20px)'
        : color,
      bottom: bottom + '%'
    }"
  ></div>
</template>

<script setup lang="ts">
defineProps<{
  name: string;
  color: string;
  bottom: number;
}>();
</script>

<style lang="scss" scoped>
.syrup {
  position: absolute;
  left: 0;

  width: 100%;
  height: 20%;

  z-index: 2;

  animation: pour-tea 2s 1s forwards;
}
</style>
