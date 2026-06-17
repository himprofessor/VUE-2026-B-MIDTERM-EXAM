<template>
  <BaseCard :class="{'is-completed':task.completed}">
    <div class="task-info">
      <h3>{{ task.title }}</h3>

      <span v-if="task.completed" class="badge completed-badge">
        Completed
      </span>
      <span v-else class="badge pending-badge"> Pending </span>
    </div>
    <div class="card-actions">
        <button class="status-btn" @click="$emit('toggle-complete',task.id)">{{ task.completed? 'Undo' :'complete' }}</button>
    
    <button class="delete-btn" @click="$emit('delete-task', task.id)">
      Delete
    </button>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';
defineProps({
  task: {
    type: Object,
    required: true,
  },
});

defineEmits(["delete-task","toggle-complete"]);
</script>

<style scoped>
.task-card {
  background-color: #ffffff;
  border-left: 5px solid #3498db; /* Blue accent line for pending tasks */
  border-radius: 8px;
  padding: 16px 16px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.task-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}
h1 {
  font-size: 1.1rem;
  color: #2c3e50;
  font-weight: 500;
}
.status-badge {
  font-size: 0.85rem;
  font-weight: bold;
  padding: 4px 10px;
  border-radius: 20px;
  background-color: #e8f4fd;
  color: #3498db;
}
.task-info {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
h3 {
  font-size: 1.1rem;
  color: #2c3e50;
}
.task-card.is-completed {
  border-left-color: #2ecc71;
  background-color: #fafafa;
}
.task-card.is-completed h3 {
  text-decoration: line-through;
  color: #95a5a6;
}
.task-card.is-completed .status-badge {
  background-color: #e8f8f0;
  color: #2ecc71;
}

.delete-btn {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 8px 14px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.9rem;
}
.delete-btn:hover {
  background-color: #c0392b;
}
.task-card.is-completed {
  border-left-color: #2ecc71; /* Switch border color to green */
  background-color: #fafafa;
}
.badge {
  font-size: 0.8rem;
  font-weight: bold;
  padding: 4px 10px;
  border-radius: 20px;
  width: fit-content;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
.pending-badge {
  background-color: #e8f4fd;
  color: #3498db;
}
.completed-badge {
  background-color: #e8f8f0;
  color: #2ecc71;
}
.task-card.is-completed {
  border-left-color: #2ecc71; /* Switch border color to green */
  background-color: #fafafa;
}
.task-card.is-completed h3 {
  text-decoration: line-through; /* Cross out completed text */
  color: #95a5a6;
}
.card-actions {
  display: flex;
  gap: 8px;
}

.status-btn {
  background-color: #2ecc71;
  color: white;
  border: none;
  padding: 8px 14px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: bold;
}
.status-btn:hover {
  background-color: #27ae60;
}
.task-card.is-completed .status-btn {
  background-color: #7f8c8d;
}
.task-card.is-completed .status-btn:hover {
  background-color: #95a5a6;
}
</style>
