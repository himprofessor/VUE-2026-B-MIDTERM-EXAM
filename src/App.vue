<template>

    <h1>📋 My Tasks</h1>
    <h3>You have {{ tasks.length }} tasks today</h3>
    
   
    <div class="add-task-form">
      <input 
        v-model="newTaskTitle"
        type="text"
        placeholder="Type a new task.."
        @keyup.enter="AddTask"
      />
      <button @click="AddTask">Add Task</button>
    </div>

    <TaskList v-if="tasks.length > 0" 
      :tasks="tasks" 
      @delete-task="deletTask"
      @toggle-complete="toggleTaskStatus"
      />

    <div v-else class="empty-state">
      <p>🎉 No tasks left! Enjoy your free time.</p>
    </div>
 
</template>

<script setup>
import { ref } from 'vue';
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

const newTaskTitle = ref('');

const AddTask = () => {
  if (!newTaskTitle.value.trim()) return;

  tasks.value.push({
    id: Date.now(),
    title: newTaskTitle.value,
    completed: false
  });
  
  newTaskTitle.value = ''; 
};

const deletTask = (id) => {

  tasks.value = tasks.value.filter(task => task.id !== id);
};

const toggleTaskStatus =(id)=>{
  tasks.value=tasks.value.map(task=>{
    if (task.id === id){
      return {...task,completed:!task.completed};
    }
    return task;
  })
}
</script>
<style  scoped>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
  background-color: #f4f6f9;
  color: #333;
  padding: 40px 20px;
}

main {
  max-width: 600px;
  margin: 0 auto;
}

h1 {
  text-align: center;
  margin-bottom: 30px;
  color: #2c3e50;
  font-size: 3rem;
}
h3{
  text-align: center;
  padding-bottom: 20px;
  padding-left: 18px;
}
.add-task-form {
  display: flex;
  gap: 10px;
  margin-bottom: 25px;
}
.add-task-form input {
  flex: 1;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
}
.add-task-form button {
  padding: 12px 20px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}
.add-task-form button:hover { background-color: #2980b9; }

.empty-state {
  background-color: #ffffff;
  border: 2px dashed #b2bec3;
  border-radius: 8px;
  padding: 30px;
  text-align: center;
  color: #7f8c8d;
  font-size: 1.1rem;
}

</style>


