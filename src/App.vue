<script setup>
import { ref } from "vue";
import TaskList from './components/TaskList.vue';

const tasks = ref([
  { id:1, title: "Finish Vue homework", completed: false},
  { id:2, title: "Buy groceries", completed: true},
  { id:3, title: "Call the dentist", completed:false}
]);

function completeTask(id) {
  const task = tasks.value.find(t => t.id === id);
  if (task) {
    task.completed = true;
  }
}

function deleteTask(id) {
  tasks.value = tasks.value.filter(t => t.id !== id)

}
</script>

<template>
  <div class="app-container">
    <h1>My Tasks</h1>
    <p class="task-count">
    You have {{ tasks.length }} tasks today
</p>
    <TaskList
    :tasks="tasks"
    @complete-task="completeTask"
    @delete-task="deleteTask"
    />
  </div>
</template>

<style scoped>
.container {
  max-width: 700px;
  margin: 30px auto;
  font-family: Arial, Helvetica, sans-serif;
  
}

h1 {
  text-align: center;
}

.task-count {
  text-align: center;
  color: #4a4a4a;
  margin-bottom: 25px;
}
</style>
