<template>
  <div class="task-list-container">
    <div v-if="tasks.length === 0" class="empty-state">
      <h1> The container that renders all task cards.</h1>
      <p> 🎉 No tasks left!                   │
│        Enjoy your free time. </p>
    </div>

    <!-- Task List Render -->
    <div v-else class="task-list">
      <BaseCard v-for="task in tasks" :key="task.id">
        <!-- Task Content -->
        <span :class="{ 'completed-text': task.completed }">
          {{ task.text }}
        </span>

        <!-- Task Actions -->
        <div class="task-actions">
          <button 
            @click="$emit('complete-task', task.id)" 
            class="btn-complete"
          >
            {{ task.completed ? 'Undo' : 'Complete' }}
          </button>

          <button 
            @click="$emit('delete-task', task.id)" 
            class="btn-delete"
          >
            Delete
          </button>
        </div>
      </BaseCard>
    </div>
  </div>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
  tasks: {
    type: Array,
    required: true
  }
});

defineEmits(['complete-task', 'delete-task']);
</script>

<style scoped>
.task-list-container {
  max-width: 700px;
  margin: 0 auto;
  padding: 16px;
}

.empty-state {
  text-align: center;
  padding: 35px;
  color: #898684;
  background-color: #dce8e0;
  border: 2px dashed #a2e605;
  border-radius: 10px;
}

.completed-text {
  text-decoration: line-through;
  color:rgb(79, 79, 126);
}

.task-actions {
  display: flex;
  gap: 8px;
}
button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-weight: 500;
  transition: background-color 0.2s;
}

.btn-complete {
  background-color: #17e980;
  color: white;
}

.btn-complete:hover {
  background-color: #cbe0d0;
}

.btn-delete {
  background-color: #ee6565;
  color: white;
}

.btn-delete:hover {
  background-color: #feb2b2;
}
</style>

