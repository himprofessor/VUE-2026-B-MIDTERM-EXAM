<template>
  <div class="task-list-container">
    <div v-if="tasks.length > 0">
      <TaskCard 
        v-for="item in tasks" 
        :key="item.id" 
        :task="item"
        @complete-task="$emit('complete-item', $event)"
        @delete-task="$emit('delete-item', $event)"
      />
    </div>
    
    <div v-else class="empty-state">
      <div class="empty-icon">🎉</div>
      <h2>No tasks left!</h2>
      <p>Enjoy your free time.</p>
    </div>
  </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue'; 


defineProps({
  tasks: {
    type: Array,
    required: true
  }
});


defineEmits(['complete-item', 'delete-item']);
</script>

<style scoped>
.task-list-container {
  margin-top: 1.5rem;
}

.empty-state {
  text-align: center;
  padding: 3rem 1.5rem;
  background-color: #f9fafb;
  border: 2px dashed #e5e7eb;
  border-radius: 12px;
  color: #6b7280;
}

.empty-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.empty-state h2 {
  margin: 0 0 0.5rem 0;
  color: #374151;
  font-size: 1.35rem;
}

.empty-state p {
  margin: 0;
  font-size: 1rem;
}
</style>
