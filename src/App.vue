<template>
  <div
    class="task"
    style="
      font-family: Arial, Helvetica, sans-serif;
      width: 100%;
      height: auto;
      border: 1px solid blue;
      border-radius: 10px;
      padding: 10px;
      margin: auto;
      background-color: white;
    "
  >
    <h1 style="font-size: ">📋 My Tasks</h1>
    <p>You have {{ totalTask }} tasks today</p>
    <hr />
    <TaskCard
      v-for="item in tasks"
      :key="item.id"
      :tasks="item"
      @complete="completeTask"
      @delete="deleteTask"
    />
    <TaskList :tasks="tasks" />
  </div>
</template>

<script setup>
import TaskCard from "./components/TaskCard.vue";
import { ref, computed } from "vue";
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

const totalTask = computed(() => tasks.value.length);

const selectTask = ref(null);

function completeTask(id) {
  const task = tasks.value.find((t) => t.id === id);
  if (task) {
    task.completed = true;
  }
  selectTask.value = null;
}

function deleteTask(id) {
  tasks.value = tasks.value.filter((t) => t.id !== id);

  if (selectTask.value !== null && selectTask.value.id === id) {
    selectTask.value = null;
  }
}
</script>

<style lang="scss" scoped>
</style>