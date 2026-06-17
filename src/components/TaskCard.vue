<template>
  <BaseCard>
    <template #header>
      <h3>
        {{ task.title }}
        <span v-if="task.completed" class="done-badge">Done</span>
      </h3>
    </template>
 
    <template #default>
      <p class="status-text">
        Status:
        <span :class="['status-badge', task.completed ? 'completed' : 'pending']">
          {{ task.completed ? 'Completed' : 'Pending' }}
        </span>
      </p>
    </template>
 
    <template #actions>
      <button class="btn btn-complete" :disabled="task.completed" @click="$emit('complete', task.id)">Complete</button>
      <button class="btn btn-delete" @click="$emit('delete', task.id)">Delete</button>
    </template>
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
</script>
 
<style scoped>
.done-badge {
  font-size: 0.8rem;
  margin-left: 8px;
  vertical-align: middle;
}
 
.status-text {
  margin: 0;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 6px;
}
 
.status-badge {
  display: inline-block;
  padding: 2px 10px;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 600;
}
 
.status-badge.pending {
  color: #92400e;
}
 
.status-badge.completed {
  color: #065f46;
}
 
.btn {
  padding: 6px 14px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 500;
  transition: opacity 0.15s;
}
 
.btn:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
 
.btn-complete {
  background: #3b82f6;
  color: white;
}
 
.btn-complete:not(:disabled):hover {
  background: #2563eb;
}
 
.btn-delete {
  background: #ef4444;
  color: white;
}
 
.btn-delete:hover {
  background: #dc2626;
}
</style>