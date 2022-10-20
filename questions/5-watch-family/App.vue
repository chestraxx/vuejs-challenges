<script setup lang="ts">
import { ref, reactive, watch } from 'vue';

const count = ref(0);

/**
 * Challenge 1: Watch once
 * Make sure the watch callback only triggers once
 */
watch(count, () => {
  console.log('Only triggered once');
});

count.value = 1;
setTimeout(() => (count.value = 1));

/**
 * Challenge 2: Watch object
 * Make sure the watch callback is triggered
 */
const state = reactive({
  count: 0,
});

watch(
  () => state.count,
  () => {
    console.log('The state.count updated');
  }
);
state.count = 2;

/**
 * Challenge 3: Callback Flush Timing
 * Make sure visited the updated eleRef
 */

const eleRef = ref();
const age = ref(2);
watch(
  age,
  () => {
    console.log(eleRef.value);
  },
  {
    flush: 'post',
  }
);
age.value = 18;
</script>

<template>
  <div>
    <p>
      {{ count }}
    </p>
    <p ref="eleRef">
      {{ age }}
    </p>
  </div>
</template>
