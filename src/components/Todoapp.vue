<template>
  <div>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="Add a new task..." />
      <button type="submit">Add</button>
    </form>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <span :style="{ textDecoration: todo.done ? 'line-through' : 'none' }">
          {{ todo.text }}
        </span>
        <button @click="toggleDone(index)">
          {{ todo.done ? 'Undo' : 'Done' }}
        </button>
        <button @click="removeTodo(index)">❌</button>
      </li>
    </ul>
    <button v-if="todos.length" @click="clearTodos" class="clear-button">
        Clear All
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos = ref([])

function addTodo() {
  if (newTodo.value.trim() === '') return

  todos.value.push({ text: newTodo.value, done: false })
  newTodo.value = ''
}

//testing 

function toggleDone(index) {
  todos.value[index].done = !todos.value[index].done
}

function removeTodo(index) {
  todos.value.splice(index, 1)
}

function clearTodos() {
  const confirmed = confirm('Are you sure you want to clear all todos?')
  if (confirmed) {
    todos.value = []
  }
}
</script>

<style scoped>
form {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
input {
  flex: 1;
  padding: 0.5rem;
  font-size: 1rem;
}
button {
  padding: 0.5rem;
  font-size: 0.9rem;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #eee;
  margin-bottom: 0.5rem;
  padding: 0.5rem;
  border-radius: 5px;
}

.clear-button {
  background: #ff4d4d;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  font-weight: bold;
  border-radius: 5px;
  margin-top: 1rem;
  cursor: pointer;
  transition: background 0.3s;
}

.clear-button:hover {
  background: #e60000;
}

.test {
  color: red;
  font-size: 2rem;
  font-weight: bold;
}
</style>