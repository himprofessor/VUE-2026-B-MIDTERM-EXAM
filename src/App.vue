<template>
  <div id="app">
    <h1>📋 My Tasks</h1>
    <p>You have {{ tasks.length }} tasks today !</p>
    <TaskList 
      :tasks="tasks" 
      @complete-task="toggleComplete" 
      @delete-task="deleteTask" 
    />
  </div>
</template>
<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
const tasks = ref([
  {
    id: 1,
    text: "Finish Vue homework", 
    completed: false
  },
  {
    id: 2,
    text: "Buy groceries",
    completed: true
  },
  {
    id: 3,
    text: "Call the dentist",
    completed: false
  },
  {
    id: 4,
    text: "Read one chapter of a book",
    completed: false
  }
]);

const toggleComplete = (taskId) => {
  const task = tasks.value.find(t => t.id === taskId);
  if (task) {
    task.completed = !task.completed;
  }
};

const deleteTask = (taskId) => {
  const index = tasks.value.findIndex(t => t.id === taskId);
  if (index !== -1) {
    tasks.value.splice(index, 1);
  }
};
</script>

<style scoped>
#app {
  font-family: sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}
h1 {
  font-size: 2.25rem;
  font-weight: 700;
  color: #1b8ebb;
  text-align: center;
  margin-top: 2rem;
  margin-bottom: 1.5rem;
  letter-spacing: -0.025em;
}
p {
  font-size: 1.235rem;
  color: #5b5f66;
  
  text-align: center;
  margin-bottom: 2rem;
}
</style>
