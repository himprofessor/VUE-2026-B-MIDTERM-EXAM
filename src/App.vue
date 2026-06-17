<!-- src/App.vue -->
<template>
  <div id="app">
    <h1>Task Management Application</h1>
    
    <TaskList 
      :tasks="tasks" 
      @done="completeTask" 
      @complete="completeTask" 
      @delete="deleteTask"
    />

    <CompleteTask 
      :task="selectedTask" 
      @done="completeTask" 
      @complete="completeTask" 
      @delete="deleteTask"
      
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import CompleteTask from './components/TaskCard.vue';
import TaskList from './components/TaskList.vue';

const tasks = ref(
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
);

const selectedTask = ref(null);

const completeTask = (taskId) => {
  tasks.value = tasks.value.map(task => {
    if (task.id === taskId) {
      return {
        ...task,
        completed: !task.completed
      };
    }
    return task;
  });
};

const deleteTask = (taskId) =>{
  tasks.value = tasks.value.filter(task => task.id !== taskId);
  if (selectedTask.value && selectedTask.value.id === taskId) {
    selectedTask.value = null;
  }
};


 

<style>
#app {
  font-family: sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
</style>