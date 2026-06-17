<script setup>
import { compile, ref } from 'vue'
import TaskList from './components/TaskList.vue' 
import TaskCard from './components/TaskCard.vue'



// 1. Reactive state for tasks and the input text
const newTask = ref('')
const tasks = ref([
  { id: 1, text: 'Finish Vue homework', completed: false },
  { id: 2, text: 'Buy groceries', completed: true }
])

// 2. Logic to add a new task
const addTask = () => {
  if (!newTask.value.trim()) return
  
  tasks.value.push({
    id: Date.now(),
    text: newTask.value,
    completed: false
  })
  
  newTask.value = '' // Clear input
}

// 3. Logic to delete a task
const deleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id)
}
</script>

<template>
  <div class="task-app">
    <h1>My Task List</h1>
    <p>You have 3 tasks today</p>

    <!-- Task Input Form -->
    <form @submit.prevent="addTask">
      <input 
        v-model="newTask" 
        placeholder="What needs to be done?" 
        type="text"
      />
      <button type="submit">Add Task</button>
    </form>

    <!-- Task Rendering -->
    <ul v-if="tasks.length > 0">
      <li 
        v-for="task in tasks" 
        :key="task.id"
        :class="{ completed: task.completed }"
      >
        <div class="task-item">
          <input type="checkbox" v-model="task.completed" />
          <span>{{ task.text }}</span>
          <button @click="completedTask(task.id)" class="completed-btn">Complete</button>
        </div>
        <button @click="deleteTask(task.id)" class="delete-btn">Delete</button>
      </li>
    </ul>
    
    <p v-else>No tasks left! enjoy your free time</p>
  </div>
</template>

<style scoped>
.task-app {
  max-width: 400px;
  margin: 2rem auto;
  font-family: sans-serif;
}
form {
  display: flex;
  gap: 10px;
  margin-bottom: 1rem;
}
input[type="text"] {
  flex: 1;
  padding: 8px;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  border-bottom: 1px solid #eee;
}
.task-item {
  display: flex;
  align-items: center;
  gap: 8px;
}
/* .completed span {
  text-decoration: line-through;
  color: #888;
} */
.delete-btn {
  background-color: #ff4444;
  color: white;
  border: none;
  padding: 4px 8px;
  cursor: pointer;
}
.completed-btn {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 4px 8px;
  cursor: pointer;
  display: flex;
  align-items: center;

}
</style>
