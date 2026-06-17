<template>
  <div class="task-list">
    <TaskCard 
      v-for="task in tasks" :key="task.id" :task="task"
      @delete-task="$emit('delete-task', $event)"
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

defineEmits(['delete-task']);
</script>