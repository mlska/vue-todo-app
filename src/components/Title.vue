<script setup>
defineProps({
  person: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <h1>Hello {{ person }}, welcome in Todo App!</h1>
</template>

<style scoped></style>
