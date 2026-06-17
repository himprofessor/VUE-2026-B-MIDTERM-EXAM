<template>
  <div class="app">
    <div class="app-card">
      <div class="app-header">
        <div>
          <h2 class="app-title">My Tasks</h2>
          <p> You have 4 tasks today</p>
        </div>
      </div>
 
      <TaskList :tasks="tasks" @complete="handleComplete" @delete="handleDelete"/>
    </div>
  </div>
</template>
 
<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
 
const tasks = ref([
  { id: 1, title: 'Finish Vue homework', completed: false},
  { id: 2, title: 'Buy groceries', completed: true},
  { id: 3, title: 'Call the dentist', completed: false},
  { id: 4, title: 'Read one chapter of a book', completed: false}
]);
 
function handleComplete(id) {
  const task = tasks.value.find(t => t.id === id);
  if (task) task.completed = true;
}
 
function handleDelete(id) {
  tasks.value = tasks.value.filter(t => t.id !== id);
}
</script>
 
<style>
* {
  box-sizing: border-box;
}
 
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  min-height: 100vh;
}
 
.app {
  display: flex;
  justify-content: center;
  padding: 40px 16px;
}
 
.app-card {
  border-radius: 14px;
  padding: 24px;
  width: 100%;
  max-width: 520px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
}
 
.app-header {
  display: flex;
  align-items: center;
  gap: 12px;
  border-bottom: 1px solid #e5e7eb;
  padding-bottom: 16px;
}
 
.app-icon {
  font-size: 1.6rem;
}
 
.app-title {
  margin: 0;
  font-size: 1.2rem;
  font-weight: 700;
}
 

</style>