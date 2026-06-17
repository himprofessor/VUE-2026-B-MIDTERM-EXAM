<template>
  <BaseCard>
    <div class="border p-4 rounded shadow-lg gap-2 flex flex-col justify-center items-center text-center mb-2 py-2 px-2">
      <div class="flex gap-2 justify-between items-center mb-2">
        <h3 class="text-2xl font-bold text-gray-800">{{ task.title }}</h3>
        <button class="text-xl bg-emerald-500 border text-white rounded px-2 py-1">Done</button>
      </div>
      
      <p class="text-sm text-gray-500 mb-4">Completed: {{ task.completed }}</p>

      <div class="flex gap-2 justify-center">
        <button
          @click="emit('task-complete', task.id)"
          class="bg-emerald-500 text-white text-xs px-3 py-1.5 rounded hover:bg-emerald-600"
        >
          Complete
        </button>

        <button
          @click="emit('delete-task', task.id)"
          class="bg-red-500 text-white text-xs px-3 py-1.5 rounded hover:bg-red-600"
        >
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue'

defineProps({
  task: Object,
})

const emit = defineEmits(['task-complete', 'delete-task'])
</script>
