<template>
  <div class="flex items-center jusify-center flex-col">
    <Header :numberOfTask="tasks.length" />
    <main class="flex flex-col gap-x-8 items-center justify-center w-6/12 h-screen">

      <div>
        <TaskList
          :tasks="tasks"
          @mark-complete="markComplete"
          @delete-task="DeleteTask"
        />
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import TaskList from "./components/TaskList.vue";


const tasks = [
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
];

const markComplete = (id) => {
  const task = tasks.value.find((task) => task.id === id);
  task.completed = true;
};

const DeleteTask = (id) => {
  const index = tasks.value.findIndex((task) => task.id === id);
  if (index !== -1) {
    tasks.value.splice(index, 1);
  }
};

</script>

<style scoped></style>
