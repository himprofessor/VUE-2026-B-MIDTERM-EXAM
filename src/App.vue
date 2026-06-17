<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([
  { id: 1, title: "Finish Vue homework", completed: false },
  { id: 2, title: "Buy groceries", completed: true },
  { id: 3, title: "Call the dentist", completed: false },
  { id: 4, title: "Read one chapter of a book", completed: false }
]);

const props = defineProps({
  tasks: {
    type: String,
    required: true
  },
});

const viewTaskDetails = (task) => {
  alert(`Viewing details for task ID: ${task.id}\nTitle: ${task.title}`);
}

const deleteTask = (task) => {
  tasks.value = tasks.value.filter(t => t.id !== task.id);
}


const completeTask = (task) => {
  const targetTask = tasks.value.find(t => t.id === task.id);
  if (targetTask) {
    targetTask.completed = !targetTask.completed;
  }
}
</script>

<template>
 
  <header class="nav">
    <h1>My Daily Tasks !</h1>
  </header>

  <main class="content">
    
    <TaskList 
      :tasks="tasks" 
      @viewTaskDetails="viewTaskDetails" 
      @completeTask="completeTask" 
      @deleteTask="deleteTask" 
    />
  </main>
</template>

<style scoped>

.nav {
  width: 100%;
  min-height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: aqua;
  color: black;
}
.nav h1 {
  font-size: 1.5rem;
  margin: 0;
}
.content {
  padding: 20px;
}
</style>
