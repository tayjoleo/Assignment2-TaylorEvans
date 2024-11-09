<template>
    <h1>Todo List</h1>
    <div v-for="todo in todos" :key="todo.id">
      <h2>{{ todo.title }}</h2>
    </div>
  </template>

<script setup>
import { ref } from 'vue';

const todos = ref([
  { id: 1, title: "Hello", completed: false },
  { id: 2, title: "World", completed: false }
]);
</script>

<style scoped>
</style>
