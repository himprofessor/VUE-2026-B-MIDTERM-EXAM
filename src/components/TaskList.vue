<template>
  <div class="task-list">
    <div v-if="tasks.length === 0" class="empty-state">
      <p>No tasks left!</p>
      <p>Enjoy your free time.</p>
    </div>
    <TaskCard v-for="task in tasks" :key="task.id" :task="task" @complete="$emit('complete', $event)" @delete="$emit('delete', $event)"/></div>
</template>
 
<script setup>
import TaskCard from './TaskCard.vue';
 
defineProps({
  tasks: {
    type: Array,
    required: true
  }
});

</script>
 
<style scoped>
.task-list {
  display: flex;
  flex-direction: column;
  gap: 14px;
}
 
.empty-state {
  text-align: center;
  padding: 40px 20px;
  font-size: 1rem;
}
 
.empty-state p {
  margin: 4px 0;
}
</style>