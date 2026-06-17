<template>
  <BaseCard>
    <div class="task-card-content">
      <div class="task-header">
        <h3>{{ task.title }}</h3>
      </div>
      <div v-if="task.completed === 'true'"> 
        <p class="done">✅ Done</p>
        <p>Status : <span  class="completed">Completed</span></p>
    </div>
      <div v-else-if="task.completed === 'false'" > 
       <p>Status : <span class="pending">Pending</span></p>
    </div>
        <div class="buttons">
        <button>Complete</button>
        <button @click="$emit('delete-task', task.id)"> Delete </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue';

// Defining Props
defineProps({
  task: {
    type: Object,
    required: true
  }
});
// Defining Emits
defineEmits(['delete-task']);
</script>

<style scoped>
.task-card-content {
  display: flex;
  flex-direction: column;
}
.task-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.completed {
  color: #16a34a; /* Green */
}
.pending {
  color: #d97706;
  font-weight: bold;
}
.done {
    color: #16a34a;
  font-weight: bold;

}
.buttons {
  margin-top: 2px;
  display: flex;
  gap: 4px;
}
button {
  cursor: pointer;
  background: none;
  border: 1px solid #777;
  padding: 4px 6px;
  border-radius: 6px;
}
</style>