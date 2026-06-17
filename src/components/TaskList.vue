<template>
  <div class="task-list">
    <TaskCard
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @delete="onDelete"
      @completed="onCompleted"
    />
    <div v-if="tasks.length === 0" class="empty">No Task available.</div>
  </div>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'
import TaskCard from './TaskCard.vue'

const props = defineProps({
  tasks: { type: Array, required: true },
})

const emit = defineEmits(['delete', 'completed'])

function onCompleted(task) {
  emit('completed', task)
}

function onDelete(id) {
  emit('delete', id)
}
</script>

<style scoped>
.task-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 12px;
}
.empty {
  color: #888;
  padding: 16px;
}
</style>



