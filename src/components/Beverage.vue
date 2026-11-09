<template>
  <Mug>
    <!-- Hot or Cold -->
    <Cold v-if="isIced" />
    <Hot v-else />

    <Contents>
      <!-- Creamer -->
      <template v-slot:top>
        <Creamer
          v-if="hasCreamer"
          :color="creamer.color"
          :bottom="80"
        />
      </template>

      <!-- Syrup -->
      <template v-slot:mid>
        <Syrup
          v-if="hasSyrup"
          :name="syrup.name"
          :color="syrup.color"
          :bottom="baseHeight"
        />
      </template>

      <!-- Base Beverage -->
      <template v-slot:bottom>
        <Base
          :color="base.color"
          :height="baseHeight"
        />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import { computed } from "vue";

import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

import type {
  BaseBeverageType,
  CreamerType,
  SyrupType,
} from "../stores/beverage";

const props = defineProps<{
  isIced: boolean;
  base: BaseBeverageType;
  creamer: CreamerType;
  syrup: SyrupType;
}>();

const hasCreamer = computed(
  () => props.creamer.id !== "c1"
);

const hasSyrup = computed(
  () => props.syrup.id !== "s1"
);

const baseHeight = computed(() => {
  let height = 100;

  if (hasCreamer.value) {
    height -= 20;
  }

  if (hasSyrup.value) {
    height -= 20;
  }

  return height;
});
</script>
