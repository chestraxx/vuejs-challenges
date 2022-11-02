<script setup lang="ts">
/**
 * Implement the custom directive
 * Make sure the `onClick` method only gets triggered once when clicked many times quickly
 * And you also need to support the debounce delay time option. e.g `v-debounce-click:ms`
 *
 */

const VDebounceClick = {
  created(el, binding) {
    const { arg: delay, value: callback } = binding;
    el.addEventListener('click', dedounce(callback, delay));
  },
};

function dedounce(fn, delay) {

  return (args) => {
    if (fn.timer) return;

    fn.call(this, args);

    fn.timer = setTimeout(() => {
      clearTimeout(fn.timer);
      fn.timer = null;
    }, delay);

  };
}

function onClick() {
  console.log('Only triggered once when clicked many times quickly');
}
</script>

<template>
  <button v-debounce-click:200="onClick">Click on it many times quickly</button>
</template>
