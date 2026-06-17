<template>
  <BaseCard>
    <div class="task-card-content">
      <div class="task-info">
        <h3 :class="{ 'title-completed': task.completed }">
          {{ task.title }}
        </h3>
        
        <div class="status-badge" :class="task.completed ? 'badge-success' : 'badge-pending'">

          {{ task.completed ? 'Completed' : 'Pending' }}
        </div>
      </div>

      <div class="task-actions">
        <button 
          v-if="!task.completed"
          @click="$emit('complete-task', task.id)" 
          class="btn btn-complete"
        >
          Complete
        </button>
        <button 
          @click="$emit('delete-task', task.id)" 
          class="btn btn-delete"
        >
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
  task: {
    type: Object,
    required: true
  }
});

defineEmits(['complete-task', 'delete-task']);
</script>

<style scoped>
.task-card-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}
.task-info {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
h3 {
  margin: 0;
  font-size: 1.15rem;
  color: #1f2937;
  font-weight: 600;
}
.title-completed {
  text-decoration: line-through;
  color: #9ca3af;
}
.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  font-size: 0.8rem;
  font-weight: 600;
  padding: 0.25rem 0.7rem;
  border-radius: 9999px;
  width: fit-content;
}
.badge-pending {
  background-color: #fef3c7;
  color: #d97706;
}
.badge-success {
  background-color: #d1fae5;
  color: #059669;
}
.status-dot {
  font-size: 0.65rem;
}
.task-actions {
  display: flex;
  gap: 0.5rem;
}
.btn {
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  font-weight: 500;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s;
}
.btn-complete {
  background-color: #2563eb;
  color: white;
}
.btn-complete:hover {
  background-color: #1d4ed8;
}
.btn-delete {
  background-color: #ef4444;
  color: white;
}
.btn-delete:hover {
  background-color: #dc2626;
}
</style>
