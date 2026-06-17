<script setup>
defineProps({
  task: {
    type: Object,
    required: true
  }
});
defineEmits(['toggle-complete', 'delete']);
</script>
<template>
  <div class="task-card" :class="{ 'is-completed': task.completed }">
    <div class="task-info">
      <h1> A single card showing one task's title, status, and buttons.</h1>
      <!-- Status Badge -->
      <span :class="['badge', task.completed ? 'badge-complete' : 'badge-pending']">
        {{ task.completed ? 'Done' : 'Pending' }}
      </span>
      
      <!-- Task Title -->
      <span class="task-title">{{ task.text }}</span>
    </div>

    <!-- Action Buttons -->
    <div class="task-actions">
      <button 
        @click="$emit('toggle-complete', task.id)" 
        class="btn btn-status"
      >
        {{ task.completed ? 'Undo' : 'Complete' }}
      </button>
      
      <button 
        @click="$emit('delete', task.id)" 
        class="btn btn-delete"
      >
        Delete
      </button>
    </div>
  </div>
</template>

<style scoped>
.task-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  background-color: #cc1d1d;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  margin-bottom: 8px;
  box-shadow: 0 1px 3px rgba(219, 39, 39, 0.05);
}

.task-card.is-completed {
  background-color: #f8fafc;
  border-color: #cbd5e1;
}

.task-info {
  display: flex;
  align-items: center;
  gap: 12px;
}

.task-title {
  font-size: 1rem;
  color: #4267a3;
}

.is-completed .task-title {
  text-decoration: line-through;
  color: #94a3b8;
}

/* Badges */
.badge {
  padding: 4px 8px;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 4px;
  text-transform: uppercase;
}

.badge-pending {
  background-color: #fef3c7;
  color: #d97706;
}

.badge-complete {
  background-color: #dcfce7;
  color: #15803d;
}

/* Buttons */
.task-actions {
  display: flex;
  gap: 8px;
}

.btn {
  padding: 6px 12px;
  font-size: 0.875rem;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
}

.btn-status {
  background-color: #3b82f6;
  color: white;
}

.is-completed .btn-status {
  background-color: #64748b;
  
}

.btn-delete {
  background-color: #ef4444;
  color: white;
}
</style>
