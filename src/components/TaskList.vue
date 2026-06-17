<template>
  <div class="mt-4">
    <div
      v-if="tasks.length === 0"
      class="text-center p-8 bg-gray-50 border rounded text-gray-500"
    >
      <p>🎉 No tasks left!</p>
      <p>Enjoy your free time.</p>
    </div>
    <div v-else>
      <TaskCard
        v-for="item in tasks"
        :key="item.id"
        :task="item"
        @complete-task="$emit('complete-task', $event)"
        @delete-task="$emit('delete-task', $event)"
      />
    </div>
  </div>
</template>

<script setup>
import TaskCard from "./TaskCard.vue";

defineProps({
  tasks: Array,
});

defineEmits(["complete-task", "delete-task"]);
</script>
