<script setup>
import { defineProps, defineEmits, toRef, ref } from 'vue';
const props = defineProps({
  modelValue: String,
  modelModifiers: { default: () => ({}) },
});

const emit = defineEmits(['update:modelValue']);

function emiteValue(e) {
  let value = e.target.value;
  if (props.modelModifiers.capitalize) {
    value = value.charAt(0).toUpperCase() + value.slice(1);
  }

  if (e.target.value !== value) {
    e.target.value = value;
  }

  emit('update:modelValue', value);
}
</script>

<template>
  <input type="text" :value="modelValue" @input.capitalize="emiteValue" />
</template>
