<template>
  <div>
    <h1>TODO App</h1>
    <TodoList :todo-list="todoList" @toggle-completed="toggleCompleted" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import { TodoList } from '@/types/todo';
import TodoList from './components/TodoList.vue';

export default defineComponent({
  name: 'App',
  components: {
    TodoList,
  },
  setup() {
    const todoList = ref<TodoList>([]);

    onMounted(() => {
      // TODO: APIからTODOリストを取得してtodoListにセットする
    });

    const toggleCompleted = (id: number) => {
      // TODO: APIを叩いてTODOアイテムのcompleted状態を更新する
      console.log(`TODO item ${id} completed toggled`);
    };

    return {
      todoList,
      toggleCompleted,
    };
  },
});
</script>
