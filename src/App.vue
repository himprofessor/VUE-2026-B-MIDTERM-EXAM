<template>
  <div class="bg-gray-100 min-h-screen p-6">
    <div class="max-w-md mx-auto bg-white p-6 rounded shadow">
      <header class="border-b pb-4">
        <h1 class="text-2xl font-bold">📋My Tasks</h1>
      </header>
      <main>
        <TaskList
          :tasks="tasks"
          @complete-task="handleComplete"
          @delete-task="handleDelete"
        />
      </main>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import TaskList from "./components/TaskList.vue";

const tasks = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false,
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true,
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false,
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false,
  },
]);

function handleComplete(id) {
  const found = tasks.value.find((t) => t.id === id);
  if (found) {
    found.completed = true;
  }
}

function handleDelete(id) {
  tasks.value = tasks.value.filter((t) => t.id !== id);
}
</script>
