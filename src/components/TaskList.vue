<template>
  <div v-if="tasks.length > 0" class="card">
    <TaskCard 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task"
      @view-task-details="$emit('viewTaskDetails', task)"
      @complete-task="$emit('completeTask', task)"
      @delete-task="$emit('deleteTask', task)"
    />
  </div>
 <div v-else class="empty-state">
    <div class="empty-icon">Don't have Task !</div>
    <p>Has no task for today, enjoy your time!</p>
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

.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 60px 20px;
  text-align: center;
  background: #f8f9fa;
  border-radius: 12px;
  border: 2px solid #dfe4ea;
  max-width: 500px;
  margin: 40px auto 0 auto;
}

.empty-icon {
  font-size: 3rem;
  margin-bottom: 16px;
}

.empty-state p {
  font-size: 1.2rem;
  color: #7f8c8d;
  font-weight: 500;
  margin: 0;
}
</style>
