<script setup>
import CustomInput from './CustomInput.vue';
import { ref } from 'vue';
const value = ref('');
</script>

<template>
  <CustomInput type="text" v-model.capitalize="value" />
</template>
