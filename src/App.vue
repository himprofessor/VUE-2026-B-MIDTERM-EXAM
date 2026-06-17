<template>
  <div class="app">
    <h1>My Tasks</h1>
     
    <TaskList 
    :tasks="tasks" 
    @delete="deleteTask" 
    @completed="completed"
    
    />
  </div>
  <TaskCompleted v-if="selected" :task="selected" @close="selected = completed" />
</template>

<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue'

const tasks = [
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  }
];

const selected = ref(null)

function completed(task) {
  selected.value = task
}

function deleteTask(id) {
  const idx = tasks.value.findIndex((t) => t.id === id)
  if (idx !== -1) tasks.value.splice(idx, 1)
  if (selected.value && selected.value.id === id) selected.value = null
}

</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}
.app {
  max-width: 880px;
  margin: 28px auto;
  padding: 0 16px;
}
h1 {
  text-align: center;
  margin-bottom: 18px;
}
</style>
