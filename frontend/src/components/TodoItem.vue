<template>
  <li>
    <input type="checkbox" :checked="item.completed" @change="toggleCompleted">
    <span :class="{ completed: item.completed }">{{ item.title }}</span>
  </li>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { TodoItem } from '@/types/todo';

export default defineComponent({
  name: 'TodoItem',
  props: {
    item: {
      type: Object as PropType<TodoItem>,
      required: true,
    },
  },
  emits: ['toggle-completed'],

  setup(props, { emit }) {
    const toggleCompleted = () => {
      emit('toggle-completed', props.item.id);
    };
    return {
      toggleCompleted,
    };
  },
});
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>
