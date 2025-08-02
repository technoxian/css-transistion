<template>
  <div class="app">
    <h1>Vue To-Do List</h1>
    <TodoApp />
  </div>
</template>

<script setup>
import TodoApp from './components/TodoApp.vue'
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background: #f4f4f4;
  margin: 0;
  padding: 2rem;
}
.app {
  max-width: 500px;
  margin: auto;
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 0 10px #ccc;
}
</style>
