<template>
  <div class="min-h-screen bg-gray-50 p-6">
    <BaseCard>
      <template #header>
        <h2 class="text-xl font-bold text-teal-600"> Task Managements </h2>
        <p class="text-sm text-blue-500 mt-1">You have {{ pendingTasksCount }} tasks today</p>
      </template>
      <p v-if="noTaskAvailable" class="text-green-500 text-sm mt-1">No tasks left!  <br>Enjoy your free time!</p>
      
      <TaskList 
        :tasks="tasks" 
        @complete-task="completeTask"
        @delete-task="deleteTask"/>
    </BaseCard>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import BaseCard from './components/BaseCard.vue';
import TaskList from './components/TaskList.vue';

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
]);
const noTask = ref([
  {
    id: 5,
    title: "No tasks available",
    completed: false
  }
]);

const noTaskAvailable = computed(() => {
  return tasks.value.length === 0;
});

const pendingTasksCount = computed(() => {
  return tasks.value.filter(task => !task.completed).length;
});

const completeTask = (id) => {
  const task = tasks.value.find(t => t.id === id);
  if (task) task.completed = true;
};

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(t => t.id !== id);
};
</script>


