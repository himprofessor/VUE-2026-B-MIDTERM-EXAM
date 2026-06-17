<template>
  <div class="card">
    <TaskCard 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task"
      @view-task-details="$emit('viewTaskDetails', task)"
      @complete-task="$emit('completeTask', task)"
      @delete-task="$emit('deleteTask', task)"
    />
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

defineEmits(["viewTaskDetails", "completeTask", "deleteTask"]);
</script>

<style scoped>
.card {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  box-sizing: border-box;
}
</style>
