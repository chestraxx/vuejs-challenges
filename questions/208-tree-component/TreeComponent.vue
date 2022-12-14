<script setup lang="ts">
interface TreeData {
  key: string;
  title: string;
  children: TreeData[];
}
defineProps<{ data: TreeData[] }>();
</script>

<template>
  <template v-for="parent in data" :key="parent.key">
    {{ parent.title
    }}<TreeComponent
      v-if="parent.children && parent.children.length"
      :data="parent.children"
    ></TreeComponent>
  </template>
</template>
