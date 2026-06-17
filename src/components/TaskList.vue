<script setup>
import TaskCard from './TaskCard.vue';

defineProps({
  tasks: {
    type: Array,
    required: true
  }
});


const emit = defineEmits(['complete', 'delete']);
</script>

<template>
  <div class="task-list">
    <p v-if="tasks.length === 0" class="empty-message">No tasks available.</p>
    
    
    <TaskCard 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task" 
      @complete="(id) => emit('complete', id)"
      @delete="(id) => emit('delete', id)"
    />
  </div>
</template>

<style scoped>
.task-list {
  max-width: 500px;
  margin: 0 auto;
}
.empty-message {
  text-align: center;
  color: #7f8c8d;
}
</style>
