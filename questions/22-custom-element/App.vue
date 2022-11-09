<script setup lang="ts">
import { defineCustomElement, h, onMounted } from 'vue';

/**
 * Implement the code to create a custom element.
 * Make the output of page show "Hello Vue.js".
 */
const VueJs = defineCustomElement({
  /* component options */
  props: {
    message: String,
  },
  emits: {},
  // template: `<span>{{message}}</span>`,
  // styles: [`/* inlined css */`],
  render() {
    return h('span', '', this.message);
  },
});

customElements.define('vue-js', VueJs);

onMounted(() => {
  document.getElementById('app')!.innerHTML =
    '<vue-js message="Hello Vue.js"></vue-js>';
});
</script>

<template>
  <div id="app"></div>
</template>
