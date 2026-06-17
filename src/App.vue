<script setup>
import { ref, computed } from 'vue';

import TaskList from './components/TaskList.vue';
import BaseCard from './components/BaseCard.vue';

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
])

const totalTask = computed(() => {
  return tasks.value.length
})
const handleDelete = (id) => {
  if (confirm('Are you sure you want to delete this task?')) {
    tasks.value = tasks.value.filter(task => task.id !== id);
    handleCloseDetail();
  }
}
const handleComplete = (id) => {
  tasks.value.forEach((task) => {
    if (task.id == id) {
      task.completed = true
    }
    console.log(task.completed)
  })
}
</script>

<template>

  <body class="h-screen bg-blue-100">
    <header class="p-4">
      <h1 class="text-center text-4xl font-bold text-blue-900 mb-2">📋 My Task</h1>
      <p v-if="totalTask > 0" class="text-center">You have {{ totalTask }} tasks today </p>
    </header>

    <main class="p-4">
      <div v-if="totalTask > 0">
        <TaskList :tasks="tasks" @complete="handleComplete" @delete="handleDelete"></TaskList>
      </div>

      <div v-else class="flex flex-col items-center">
        <BaseCard>
          <p>🎉 No tasks left!</p>
          <p>Enjoy your free time.</p>
        </BaseCard>
      </div>
    </main>
  </body>
</template>
