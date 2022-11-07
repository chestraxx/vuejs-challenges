<script setup lang="ts">
import { ref, h } from 'vue';

/**
 * Implement a functional component :
 * 1. Render the list elements (ul/li) with the list data
 * 2. Change the list item text color to red when clicked.
 */
const ListComponent = (props, { slots, emit, attrs }) => {
  const { list, activeIndex } = props;
  const handleToggle = (idx) => emit('toggle', idx);
  const li = list.map((li, index) => {
    return h(
      'li',
      {
        key: index,
        style: index === activeIndex ? 'color: red;' : undefined,
        onClick: () => handleToggle(index),
      },
      li.name
    );
  });

  return h('ul', {}, li);
};
ListComponent.props = ['list', 'activeIndex'];

const list = [
  {
    name: 'John',
  },
  {
    name: 'Doe',
  },
  {
    name: 'Smith',
  },
];

const activeIndex = ref(0);

function toggle(index: number) {
  activeIndex.value = index;
}
</script>

<template>
  <list-component :list="list" :active-index="activeIndex" @toggle="toggle" />
</template>
