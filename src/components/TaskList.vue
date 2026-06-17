<template>
  <div class="task-list">
    <TaskCard 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task"
      @complete="$emit('complete', $event)"
      @delete="$emit('delete', $event)"
    />
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import TaskCard from './TaskCard.vue';

const props = defineProps({
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
  gap: 16px;
}
</style>
