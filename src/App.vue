<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base="selectedBase"
      :creamer="selectedCreamer"
      :syrup="selectedSyrup"
    />

    <ul>
      <!-- Temperature Selection -->
      <li>
        <label v-for="temp in temps" :key="temp">
          <input
            type="radio"
            name="temperature"
            :value="temp"
            v-model="currentTemp"
          />
          {{ temp }}
        </label>
      </li>

      <!-- Base Beverage Selection -->
      <li>
        <label v-for="base in bases" :key="base.id">
          <input
            type="radio"
            name="base"
            :value="base.id"
            v-model="currentBase"
          />
          {{ base.name }}
        </label>
      </li>

      <!-- Syrup Selection -->
      <li>
        <label v-for="syrup in syrups" :key="syrup.id">
          <input
            type="radio"
            name="syrup"
            :value="syrup.id"
            v-model="currentSyrup"
          />
          {{ syrup.name }}
        </label>
      </li>

      <!-- Creamer Selection -->
      <li>
        <label v-for="creamer in creamers" :key="creamer.id">
          <input
            type="radio"
            name="creamer"
            :value="creamer.id"
            v-model="currentCreamer"
          />
          {{ creamer.name === "No Cream"
            ? "No Creamer"
            : creamer.name }}
        </label>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

import Beverage from "./components/Beverage.vue";

import {
  temps,
  bases,
  creamers,
  syrups,
  currentTemp,
} from "./stores/beverage";

const currentBase = ref("b2");
const currentCreamer = ref("c2");
const currentSyrup = ref("s2");

const selectedBase = computed(() =>
  bases.value.find(item => item.id === currentBase.value)!
);

const selectedCreamer = computed(() =>
  creamers.value.find(item => item.id === currentCreamer.value)!
);

const selectedSyrup = computed(() =>
  syrups.value.find(item => item.id === currentSyrup.value)!
);
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  margin: 0;

  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

ul {
  list-style: none;
}

li {
  margin-bottom: 12px;
}

label {
  margin-right: 5px;
}
</style>
