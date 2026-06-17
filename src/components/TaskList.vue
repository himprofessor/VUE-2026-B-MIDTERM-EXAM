<template>
  <div class="">
    <TaskCard
      v-for="item in tasks"
      :key="item.id"
      :task="item"
      @task-complete="(id) => emit('select-task', id)"
      @delete-task="(id) => emit('remove-task', id)"
    />
  </div>
</template>
<script setup>
import TaskCard from './TaskCard.vue'

defineProps({
  tasks: Array,
})

const emit = defineEmits(['select-task', 'remove-task'])
</script>
