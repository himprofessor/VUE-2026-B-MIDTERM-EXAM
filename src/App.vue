<template>
  <div id="app-wrapper">
    <header>
      <h1> My Tasks</h1>
      <p>We have {{ tasks.length }} tasks today</p>
    </header>

    <TaskList
      :tasks="tasks"
      @complete-task="completeTask"
      @delete-task="deleteTask"
    />
  </div>
</template>

<script setup>
import { ref } from "vue"
import TaskList from "./Components/TaskList.vue"

const tasks =ref( [
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
]);

const completeTask = (id) => {
  tasks.value.find(t => t.id === id).completed = true;
}

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
}
</script>

<style scoped>
#app-wrapper {
  max-width: 680px;
  margin: 60px auto;
  font-family: sans-serif;
}

header {
  margin-bottom: 24px;
}

header h1 {
  font-size: 28px;
  margin: 0 0 4px;
}

header p {
  color: #666;
  margin: 0;
}
</style>
