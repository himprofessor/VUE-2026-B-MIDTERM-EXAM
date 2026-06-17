<template>
  <h1 class="text-6xl">You did it!</h1>
  <div class="font-text-bold text-center text-3xl">
    <h1>Task Management</h1>
    <div class="border flex-4 px-20 rounded text-center mb-4 py-4">
      <h3>My Tasks</h3>
      <p>You have 4 tasks today</p>
      <TaskList 
      :tasks="tasks" 
      @select-task="handleViewDetail" 
      @remove-task="handleDeleteTask" />
    </div>


    <TaskComplete 
    v-if="isModalOpen" 
    :task="selectedTask" 
    @close="isModalOpen = false" 
    @complete="handleCompleteTask" />

  </div>

</template>


<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue'
import TaskCard from './components/TaskCard.vue'
import TaskComplete from './components/TaskComplete.vue';

const tasks = ref([
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
]
);


const selectedTask = ref(null)
const isModalOpen = ref(false)

const handleViewDetail = (id) => {
  const match = tasks.value.find((task) => task.id === id)
  if (match) {
    selectedTask.value = match
    isModalOpen.value = true
  }
}

const handleCompleteTask = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id)
  isModalOpen.value = false
  selectedTask.value = null
}

const handleDeleteTask = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id)


  if (selectedTask.value && selectedTask.value.id === id) {
    selectedTask.value = null
  }
}


</script>

<style scoped></style>
