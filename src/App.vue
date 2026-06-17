<template>
  <main class="app-viewport">
    <div class="app-window">
      <header class="app-header">
        <div class="title-area">
          <h1>Nita's Task</h1>
        </div>
        <p class="counter-text">
     
          I have  {{ activeTasksCount }} pending task{{ activeTasksCount === 1 ? '' : 's' }} today
        </p>
      </header>

      <TaskList 
        :tasks="tasksCollection" 
        @complete-item="handleComplete"
        @delete-item="handleDelete"
      />
    </div>
  </main>
</template>
<script setup>
import { ref, computed } from 'vue';
import TaskList from './components/TaskList.vue';

const tasksCollection = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: true
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: false
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
  },
    {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  },
    {
    id: 5,
    title: "project vue",
    completed: false
  }
]);

const activeTasksCount = computed(() => {
  return tasksCollection.value.filter(task => !task.completed).length;
});


const handleComplete = (targetId) => {
  const selectedTask = tasksCollection.value.find(task => task.id === targetId);
  if (selectedTask) {
    selectedTask.completed = true;
  }
};


const handleDelete = (targetId) => {
  tasksCollection.value = tasksCollection.value.filter(task => task.id !== targetId);
};
</script>

<style>

button, input {
  font-family: inherit;
}

body {
  margin: 0;
  padding: 0;
  background-color: #f3f4f6;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.app-viewport {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding: 2rem 1rem;
  box-sizing: border-box;
}

.app-window {
  width: 100%;
  max-width: 550px;
  background-color: transparent;
}

.app-header {
  margin-bottom: 1.5rem;
  border-bottom: 2px solid #e5e7eb;
  padding-bottom: 1rem;
}

.title-area {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.header-icon {
  font-size: 1.75rem;
}

h1 {
  margin: 0;
  font-size: 1.75rem;
  color: #beb918;
  font-weight: 700;
}

.counter-text {
  margin: 0.5rem 0 0 0;
  color: #6f94c7;
  font-size: 1rem;
}
</style>
