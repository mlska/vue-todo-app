<script setup>
import Title from "./components/Title.vue";
import ControlPanel from "./components/ControlPanel.vue";
import TodoItem from "./components/TodoItem.vue";
import { ref } from "vue";

const todos = ref([]);

const onAddTodo = (text) => {
  if (text.trim() === "") {
    return;
  }
  todos.value.push({
    id: Math.random().toString(16).slice(2),
    completed: false,
    text,
  });
};

const onRemoveTodo = (id) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};

const onCompleteTodo = (id, completed) => {
  const todo = todos.value.find((todo) => todo.id === id);
  todo.completed = completed;
};
</script>

<template>
  <Title person="Kamil" />
  <ControlPanel @addTodo="onAddTodo" />
  <TodoItem
    v-for="todo in todos"
    :key="todo.id"
    :todo="todo"
    @handleRemove="onRemoveTodo"
    @completeTodo="onCompleteTodo"
  />
</template>

<style scoped>
* {
  margin: 0;
  box-sizing: border-box;
}
</style>
