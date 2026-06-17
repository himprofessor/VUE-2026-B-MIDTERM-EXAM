

<template>
  <div class="app">
    <header class="header">

    <div class="left">
       <h1 class="title">My Task</h1> 
       <p class="subtitle"> 
        {{ tasks.length }}
        Task Today: 
       </p>
    
    </div>

    <div class="right" aria-hidden="true">
      <div class="pill">
        {{ countPading }}
        Pending
      </div>

      <div class=" pill pill-complete">
        {{  countComplete }}

        Completed
      </div>

    </div>
    </header>

    <main class="content">
      <TaskList :tasks="tasks" @complete="completeHandle" @delete="deleteHandle" />
    </main>
  </div>
  
  
</template>


<script setup>
import { ref , computed }  from 'vue'

import TaskList from './components/TaskList.vue'


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

const countPading = computed(() => {
  return tasks.value.filter(task => !task.completed).length
})


const countComplete= computed(() => {
  return tasks.value.filter(task => task.completed).length
})




const deleteHandle = (taskId) => {
  tasks.value = tasks.value.filters(task => task.id !== taskId)
}


const completeHandle = (taskId) => {
  tasks.value = tasks.value.map(task => {
    if (task.id !== taskId ) {
      return { ... task, completed: true}
    }
    return task
  })
}




</script>

<style scoped>


.app{
  max-width: 800px;
  margin: 24px auto;
  padding: 16px;

}

.header{
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 16px;
  padding: 16px 18px;
  border-radius: 14px;
  border: 1px solid gray;
  background: #514c4c;
}
.title {
  margin: 0;
  font-size: 28px;
}

.subtitle {
  margin: 6px 0 0;
  opacity: 0.9;
}

.right {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: flex-end;
}

.pill {
  padding: 6px 10px;
  border-radius: 999px;
  border: 1px solid gray;
  background: rgba(255, 255, 255, 0.03);
  font-weight: 700;
}

.pill-completed {
  border-color: green;
  color: #47dd7e;
}

.content {
  margin-top: 14px;
}
</style>
