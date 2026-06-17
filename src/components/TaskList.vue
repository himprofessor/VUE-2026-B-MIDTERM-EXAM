<template>
  <div>
    <div v-if="tasks.length === 0">
      <p>🎉 No tasks left! Enjoy your free time.</p>
    </div>
    <div v-else class="grid">
      <TaskCard 
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @complete="$emit('complete-task', $event)"
        @delete-task="$emit('remove-task', $event)"
      />
    </div>
  </div>
</template>

<script setup>
  import TaskCard from './TaskCard.vue';

  defineProps({ 
    tasks: Array 
  });
  defineEmits(['complete-task', 'remove-task']);
</script>

<style scoped>

</style>