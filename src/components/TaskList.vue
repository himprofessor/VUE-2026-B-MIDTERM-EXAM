<template>
  <div>
    <div v-if="tasks.length === 0">
      <p>🎉 No tasks left! Enjoy your free time.</p>
    </div>
    <div v-else>
         <TaskCard v-for="task in tasks" :key="task.id" :task="task" @complete="emit('complete-task', $event)" @delete="emit('delete-task', $event)"/>
    </div>
  </div>
</template>

<script setup>
import TaskCard from "./TaskCard.vue";

defineProps({
  tasks: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["complete-task", "delete-task"]);
</script>

<style lang="scss" scoped></style>
