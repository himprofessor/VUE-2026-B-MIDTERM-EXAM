<template>
  <div>
    <header>
         <h1 style="text-align: center; color: lightskyblue">
             My Tasks
          </h1>
    </header>
    <TaskList 
    :tasks="tasks"
    @delete-task="deleteTask"
    @complete-task="completeTask"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';
const tasks =ref([ 
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
const completeTask =(id)=>{
  const task=tasks.value.find(task=>task.id===id)
  if (task) task.completed=true
}

const deleteTask =(id)=>{
  tasks.value=tasks.value.filter(task=>task.id !==id)
}
</script>

<style lang="scss" scoped>

</style>

