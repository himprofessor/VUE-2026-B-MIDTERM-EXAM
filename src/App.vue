<template>
  <div class="container">
    <div class="header">
      <h1>My Tasks</h1>
      <p>You have {{ count }} tasks today</p>
    </div>
    
    <div class="filter-button">
      <div class="filter">
        <label>Filter by:</label>
        <select id="task-filter" v-model="filter">
          <option value="all">All</option>
          <option value="completed">Completed</option>
          <option value="pending">Pending</option>
        </select>
      </div>

      <div class="task-count">
        <p>Pending: {{ pendingCount }} | Completed: {{ completedCount }}</p>
      </div>

    </div>
    

    <TaskList v-if="filterTasks.length > 0"
      :tasks="filterTasks" 
      @complete="handleComplete"
      @delete="handleDelete"
    />

    <div v-else class="empty-state">
      <p>🎉 No tasks left!</p>
      <p>Enjoy your free time.</p>
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

// count
const count = computed(() => {
  return tasks.value.length;
});


// complete
const handleComplete = (id) => {
  tasks.value.forEach((task) => {
    if (task.id === id) {
      task.completed = !task.completed;
    }
  });
};

// delete
const handleDelete = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id);
};

// filter
const filter = ref("all");

const filterTasks = computed(() => {
  if (filter.value === "completed") {
    return tasks.value.filter(task => task.completed === true);
  } 
  if (filter.value === "pending") {
    return tasks.value.filter(task => task.completed === false);
  }
  return tasks.value;
});


//pending count
const pendingCount = computed(() => {
  let count = 0;
  tasks.value.forEach(task => {
    if (task.completed === false) {
      count++;
    }
  });
  return count;
});

//completed count
const completedCount = computed(() => {
  let count = 0;
  tasks.value.forEach(task => {
    if (task.completed === true) {
      count++;
    }
  });
  return count;
});



</script>

<style scoped>

.container {
  font-family: roboto, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.header {
  text-align: center;
  margin-bottom: 20px;
}

.header h1 {
  font-size: 28px;
  color: #333;
}

.header p {
  font-size: 16px;
  color: #666;
}

.empty-state {
  text-align: center;
  margin-top: 20px;
}

.empty-state p {
  font-size: 18px;
  color: #777;
}

.filter-button {
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.filter {
  display: flex;
  align-items: center;
  gap: 8px;
}

.task-count {
  display: flex;
  align-items: center;
  gap: 8px;
  color: #777;
}

#task-filter {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

</style>
