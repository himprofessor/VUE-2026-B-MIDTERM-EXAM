<template>
  <div class="text-white bg-blue-300 w-300 ml-110 rounded-lg h-80">
    <div class="text-center bg-pink-600 py-2 w-300 rounded-lg">
      <h1>My Tasks 4</h1>
      <p>You have {{ tasks.length }} tasks today</p>
    </div>
    <div>
      
      <TaskList
        :tasks="tasks" 
        @complete="buttonComplete" 
        @delete="buttonDelete" 
      />
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';


const tasks = ref ([
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


const selectedTask = ref(null);

function buttonComplete(task) {
  selectedTask.value = task;
}


function buttonDelete(taskId) {
  tasks.value = tasks.value.filter(s => s.id !== taskId);
}
</script>

<style lang="scss" scoped>
</style>




