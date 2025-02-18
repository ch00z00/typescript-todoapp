<template>
  <ul>
    <TodoItem
      v-for="item in todoList"
      :key="item.id"
      :item="item"
      @toggle-completed="toggleCompleted"
    />
  </ul>
</template>

<script setup>
import { defineComponent, PropType } from 'vue';
import { TodoList, TodoItem } from '@/types/todo';
import TodoItem from './TodoItem.vue';

export default defineComponent({
  name: 'TodoList',
  components: {
    TodoItem,
  },
  props: {
    todoList: {
      type: Array as PropType<TodoList>,
      required: true,
    },
  },
  emits: ['toggle-completed'],
  setup(props, { emit }) {
    const toggleCompleted = (id: number) => {
      emit('toggle-completed', id);
    };

    return {
      toggleCompleted,
    };
  },
</script>
