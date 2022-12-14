<script setup lang="ts">
import { ref } from 'vue';

/**
 * Implement a custom directive
 * Create a two-way binding on a form input element
 *
 */
const VOhModel = {
  mounted(el, { value: modelValue }) {
    el.value = modelValue;
    el.addEventListener('input', (event) => {
      value.value = event.target.value;
    });
  },
};

const value = ref('Hello Vue.js');
</script>

<template>
  <input v-oh-model="value" type="text" />
  <p>{{ value }}</p>
</template>
<style>
input {
  background-color: red;
}
</style>
