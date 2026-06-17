<template>
  <div class="card-contener">
    <div>
      <header>
        <h1>MY Tasks</h1>
        <p>you have {{ tasks.length }}{{ tasks.length === 1 ? "task" : "tasks" }}</p>
        <p v-if="tasks.length > 0">
          &mdash;
          <span>{{ pendingCount() }} pending</span>
          <span>{{ completeCount() }}complete</span>
        </p>
      </header>
      <TaskList :tasks="tasks" @complete-task="completeTask" @delete-task="deleteTask" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
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

const completeTask = (id) => {
  const task = tasks.value.find((t) => t.id === id);
  if (task) task.completed = true;
};
const pendingCount = () => tasks.value.filter((t) => !t.completed).length;
const completeCount = () => tasks.value.filter((t) => !t.completed).length;

const deleteTask = (id) => {
  tasks.value = tasks.value.filter((t) => t.id !== id);
};
</script>

<style scoped>
.card-contener {
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
