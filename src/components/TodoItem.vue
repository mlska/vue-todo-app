<script setup>
import { ref } from "vue";
const props = defineProps(["todo"]);
</script>

<template>
  <div class="wrapper">
    <div>
      <input
        type="checkbox"
        v-model="completed"
        @change="$emit('completeTodo', todo.id, completed)"
      />
      <span v-bind:class="{ completed: todo.completed }">{{ todo.text }}</span>
    </div>
    <button @click="$emit('handleRemove', todo.id)">Delete</button>
  </div>
</template>

<style scoped>
div {
  display: flex;
  justify-content: space-between;
}
input {
  margin-right: 16px;
}
.completed {
  text-decoration: line-through;
}
.wrapper {
  padding: 16px;
  margin: 8px 0;
  border: 1px solid black;
}
</style>
