<template>
  <main>
    <header >
      <h1 >📋 My tasks</h1>
      <p >You have 3 tasks today</p>
    </header>
    <div>
      <TaskList :tasks="tasks" @complete-task="CompleteTask" @remove-task="RemoveTask" />
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([
  { 
    id: 1, 
    title: 'Review project requirements', 
    completed: false 
  },
  { 
    id: 2, 
    title: 'Build Vue components', 
    completed: true 
  },
  { 
    id: 3, 
    title: 'Test event emission logic', 
    completed: false 
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  }
]);

const CompleteTask = (taskId) => {
  const task = tasks.value.find(t => t.id === taskId);
  if (task) {
    task.completed = true;
  }
};

const RemoveTask = (taskId) => {
  tasks.value = tasks.value.filter(t => t.id !== taskId);
};
</script>

<style scoped>
  
</style>
