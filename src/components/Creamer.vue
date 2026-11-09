<template>
  <div
    class="froth"
    :style="{
      backgroundColor: color,
      bottom: bottom + '%'
    }"
  >
    <div v-for="n in 5" :key="n" class="foam"></div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  color: string;
  bottom: number;
}>();
</script>


<style lang="scss" scoped>
.froth {
  position: absolute;
  left: 0;

  width: 100%;
  height: 15%;

  z-index: 3;

  overflow: visible;

  animation: pour-tea 2s 2s forwards;
}

.foam {
  position: absolute;

  width: 28px;
  height: 28px;

  border-radius: 50%;

  background-color: inherit;
}

.foam:nth-child(1) {
  top: -13px;
  left: 0;
}

.foam:nth-child(2) {
  top: -17px;
  left: 22px;
}

.foam:nth-child(3) {
  top: -19px;
  left: 48px;
}

.foam:nth-child(4) {
  top: -17px;
  right: 22px;
}

.foam:nth-child(5) {
  top: -13px;
  right: 0;
}

@keyframes pour-tea {
  0% {
    transform: translateY(100%);
  }

  100% {
    transform: translateY(0%);
  }
}
</style>
