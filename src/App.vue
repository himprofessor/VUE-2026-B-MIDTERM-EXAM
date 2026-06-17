<template>
  <div class="app-container">
    <header class="app-header">
      <h2>📋 My Tasks</h2>
      <p v-if="tasks.length > 0">You have {{ tasks.length }} tasks today</p>
    </header>
    <div v-if="tasks.length > 0">
      <TaskList :tasks="tasks" 
        @delete-task="DeleteTask"
      />
    </div>
    <div v-else class="empty-state">
      <p>🎉 No tasks left!</p>
      <p>Enjoy your free time.</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([
  { id: 1, title: 'Finish Vue homework', completed: 'false' },
  { id: 2, title: 'Buy groceries', completed: 'true' },
  { id: 3, title: 'Call the dentist', completed: 'false' },
  { id: 4, title: 'Read one chapter of a book', completed: 'false' }
]);


const DeleteTask = (taskId) => {
  tasks.value = tasks.value.filter(task => task.id !== taskId);
};
</script>

<style>

body {
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;

}
.app-container {
  max-width: 500px;
  margin: auto;
  background: rgba(255, 255, 255, 0.822);
  padding: 10px;
}
.empty-state {
  text-align: center;
  padding: 2rem;
  color: #555;
  font-size: 1.1rem;
}
</style>