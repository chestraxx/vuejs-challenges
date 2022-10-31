<script setup>
defineProps({
  type: {
    type: String,
    default: 'default',
    validator: (value) => {
      return ['primary' ,'ghost' ,'dashed' ,'link'  ,'text' ,'default'].indexOf(value) >= 0
    },
  },
})
</script>

<template>
  <button>Button</button>
</template>