<script setup lang="ts">
import { reactive, isReactive, toRaw, markRaw } from "vue"

const state = { count: 1 }
const reactiveState = toRaw(state)

/**
 * Modify the code so that we can make the output be true.
*/
console.log(reactiveState === state)

/**
 * Modify the code so that we can make the output be false.
*/
const info = { count: 1 }
const reactiveInfo = markRaw(info)

console.log(isReactive(reactiveInfo))

</script>

<template>
  <div>
    <p>
      {{ reactiveState.count }}
    </p>
  </div>
</template>
