
<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base="selectedBase"
      :creamer="selectedCreamer"
      :syrup="selectedSyrup"
    />

    <ul class="drink-options">
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

      <li>
        <label v-for="base in bases" :key="base.id">
          <input
            type="radio"
            name="base"
            :value="base"
            v-model="selectedBase"
          />
          {{ base.name }}
        </label>
      </li>

      <li>
        <label v-for="creamer in creamers" :key="creamer.id">
          <input
            type="radio"
            name="creamer"
            :value="creamer"
            v-model="selectedCreamer"
          />
          {{ creamer.name }}
        </label>
      </li>

      <li>
        <label v-for="syrup in syrups" :key="syrup.id">
          <input
            type="radio"
            name="syrup"
            :value="syrup"
            v-model="selectedSyrup"
          />
          {{ syrup.name }}
        </label>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Beverage from './components/Beverage.vue';

import {
  temps,
  bases,
  creamers,
  syrups,
  currentTemp
} from './stores/beverage';

const selectedBase = ref(bases.value[0]);
const selectedCreamer = ref(creamers.value[0]);
const selectedSyrup = ref(syrups.value[0]);
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(
    to bottom,
    #6e4228 0%,
    #956f5a 100%
  );
}

ul {
  list-style: none;
}

.drink-options {
  padding: 0;
  margin-top: 20px;
}

.drink-options li {
  margin: 5px 0;
}

.drink-options label {
  margin-right: 10px;
  cursor: pointer;
}
</style>
