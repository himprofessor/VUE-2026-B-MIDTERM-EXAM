<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';


const tasks = ref([
  { 
    id: 1, 
    title: 'Analyst Data', 
    description: 'To know the relational of food panda app', 
    isDone: true 
  },
  { 
    id: 2, 
    title: 'Create a wireframe', 
    description: 'To demo the look of website before start develop ', 
    isDone: false 
  },
  { 
    id: 3, 
    title: 'Review Pull Requests', 
    description: 'Check team code updates for performance optimization.', 
    isDone: false 
  }
]);


const handleComplete = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) {
    task.isDone = true;
  }
};

const handleDelete = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
};
</script>

<template>
  <div class="app-container">
    <h2>My Tasks</h2>

    <p id="para">You have {{ tasks.length }} tasks today</p>
    
   
    <TaskList 
      :tasks="tasks" 
      @complete="handleComplete"
      @delete="handleDelete"
    />
  </div>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
  margin: 0;
  padding: 20px;
}
.app-container {
  max-width: 600px;
  margin: 0 auto;
}
h2{
  text-align: center;
  color: #2c3e50;
}
#para{
  text-align: center;
}
</style>
