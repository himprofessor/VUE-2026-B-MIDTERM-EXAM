
<template>
  <div> 
    <BaseCard>
      <div class="task-header">
        <span class="task-title">{{ task.title }}</span>
        <span class="badge" :class="task.completed ? 'badge-done' : 'badge-pending'">
          {{ task.completed ? 'Done' : 'Pending' }}
        </span>
      </div>

      <p class="status-text">
        Status: 
        <span class="status-indicator" :class="task.completed ? 'dot-done' : 'dot-pending'"></span>
        <span v-if="task.completed">Completed</span>
        <span v-else>Pending</span>
      </p>

      <div class="actions">
        <button class="btn-complete" :disabled="task.completed" @click="$emit('complete-task', task.id)" >
          Complete
        </button>
        <button class="btn-delete" @click="$emit('delete-task', task.id)">
          Delete
        </button>
      </div>
    </BaseCard>
  </div> 
</template>

<script setup>
import BaseCard from "./BaseCard.vue"

defineProps({ 
  task: Object 
})

defineEmits(["complete-task", "delete-task"])
</script>

<style scoped>
.task-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
}
.badge {
  font-size: 12px;
  padding: 3px 10px;
  border-radius: 20px;
  font-weight: 600;
}
.badge-done {
  background: #dcfce7;
  color: #16a34a;
}
.badge-pending {
  background: #fef9c3;
  color: #b45309;
}
.status-text {
  font-size: 13px;
  color: #555;
  margin: 0 0 14px;
}
.dot-done {
  color: #16a34a;
}
.dot-pending {
  color: #f59e0b;
}
.actions {
  display: flex;
  gap: 10px;
}
.btn-complete {
  background: #22c55e;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 7px 16px;
  font-size: 13px;
}
.btn-complete:disabled {
  background: #a3e0b8;
  cursor: not-allowed;
}
.btn-delete {
  background: #ef4444;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 7px 16px;
  font-size: 13px;
}
</style>