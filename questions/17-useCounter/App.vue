<script setup lang="ts">
import { ref } from 'vue';

const value = ref(0);

interface UseCounterOptions {
  min?: number;
  max?: number;
}

/**
 * Implement the composable function
 * Make sure the function works correctly
 */
function useCounter(initialValue = 0, options: UseCounterOptions = {}) {
  function inc() {
    if (options.hasOwnProperty('max') && options.max === value.value) return;
    value.value++;
  }
  function dec() {
    if (options.hasOwnProperty('min') && options.min === value.value) return;
    value.value--;
  }

  function reset() {
    value.value = initialValue;
  }

  return { count: value, inc, dec, reset };
}

const { count, inc, dec, reset } = useCounter(0, { min: 0, max: 10 });
</script>

<template>
  <p>Count: {{ count }}</p>
  <button @click="inc">inc</button>
  <button @click="dec">dec</button>
  <button @click="reset">reset</button>
</template>
