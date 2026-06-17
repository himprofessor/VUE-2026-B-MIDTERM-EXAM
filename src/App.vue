<template>
  <div class="body">
    <!-- Title Tasks -->
    <div>
      <h1>My Tasks</h1>
      <p v-if="totalTask > 0">You have {{ totalTask }} tasks today</p>
      <p v-else>🎉 No tasks left! Enjoy your free time.</p>
    </div>

    <!-- Task Card -->
    <div v-for="(task, index) in tasks" :key="task.id" class="card">
      <!-- title -->
      <h3>{{ task.title }}</h3>

      <!-- Status -->
       <span>Status: </span>
      <span :style="{ color: status[task.id] ? 'green' : 'blue' }">{{ status[task.id] ?   "Completed":"Pedding" }}</span>

      <div class="btn">
        <!-- button  -->
        <button @click="actionStatus(task.id)" class="my-btn">Complete</button>
        <button @click="handleAction(index)" class="my-btn delete">Delete</button>
      </div>
    </div>
  </div>
</template>

<script setup>
// import TaskCard from "./components/TaskCard.vue";
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

// action delete
const handleAction = (index) => {
  alert(`Are you sure?`);
  tasks.value.splice(index, 1);
};

// Status: Pedding and Completed
const status = ref({});

const actionStatus = (id) => {
  status.value[id] = !status.value[id];
};

//Total task
const totalTask = computed(() => tasks.value.length);
</script>

<style>
.body {
  font-family: 'Roboto', sans-serif;
}
.card {
  border: 2px solid rgb(8, 36, 163);
  padding: 16px;
  margin-bottom: 8px;
  width: 200px;
  border-radius: 8px;
}
.btn {
  display: flex;
  justify-content: space-between;
}
.my-btn {
  background-color: #42b883;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
}
.delete {
  background-color: rgb(218, 32, 32);
}
.my-btn:hover {
  background-color: #35495e;
}
</style>
