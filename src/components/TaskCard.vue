<template>
  <BaseCard>
    <div class="flex justify-between items-center">
      <div>
        <h3 :class="{ 'line-through text-green-600': task.completed }" class="font-bold">
          {{ task.title }}
        </h3>
        <span
          v-if="task.completed"
          class="bg-green-100 text-green-700 text-xs px-2 py-1 rouded"
          >Status: Completed</span
        >
        <span
          v-else
          class="bg-yellow-100 text-green-700 text-xs px-2 py-1 rouded"
          >Status: Pending</span
        >
      </div>
      <div class="flex space-x-2">
        <button
          :disabled="task.completed"
          :class="
            task.completed
              ? 'bg-gray-300 text-gray-600 border-gray-400 cursor-not-allowed'
              : 'bg-green-600 text-white border-emerald-600'
          "
          @click="$emit('complete-task', task.id)"
          class="font-medium text-white px-2 py-1 rounded text-sm"
        >
          Complete
        </button>
        <button
          @click="$emit('delete-task', task.id)"
          class="bg-red-500 text-white px-2 py-1 rounded text-sm"
        >
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from "./BaseCard.vue";

defineProps({
  task: Object,
});

defineEmits(["complete-task", "delete-task"]);
</script>
