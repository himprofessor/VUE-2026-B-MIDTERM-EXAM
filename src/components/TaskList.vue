
<template>
  <div v-if="tasks.length === 0" class="text-center">
    <span>No tasks left. Enjoy your free time.</span>
  </div>

  <div class="flex gap-20 py-4 px-4">
    <TaskCard 
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @complete="emit('complete', $event)"
      @delete="emit('delete', $event)"
    />
  </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue'

const props = defineProps({
  tasks: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['complete', 'delete'])
</script>

<style scoped>
</style>