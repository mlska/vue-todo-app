<script setup>
import { ref } from "vue";
const emit = defineEmits(["addTodo"]);
const input = ref("");

defineExpose({
  input,
});

const addTodo = () => {
  emit("addTodo", input.value);
  input.value = "";
};
</script>

<template>
  <div>
    <input
      type="text"
      placeholder="new todo text"
      v-model="input"
      v-on:keyup.enter="addTodo"
    />
    <button @click="addTodo">Add</button>
  </div>
</template>

<style scoped>
div {
  display: flex;
  gap: 16px;
  margin: 16px 0px;
  justify-content: center;
}

input {
  padding: 12px 24px;
  margin: 0;
  border: 1px solid black;
  width: 100%;
}

button {
  padding: 0 16px;
}
</style>
