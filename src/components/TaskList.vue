<template>
  <div>
    <TaskCard 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task"
      @complete="$emit('complete-task', $event)"
      @delete="$emit('delete-task', $event)"
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

defineEmits(['complete-task', 'delete-task']);
</script>

