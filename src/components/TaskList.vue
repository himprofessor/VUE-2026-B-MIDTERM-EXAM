<template>
    <div class="task-list">
        <TaskCard
        v-for="task in tasks"
        :key="task.id"
        :task="task"
       @delete-task="(id) => $emit('delete-task', id)"
       @toggle-complete="(id)=>$emit('toggle-complete',id)"
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

defineEmits(['delete-task','toggle-complete']);
</script>

<style  scoped>
.task-list {
  display: flex;
  flex-direction: column;
  gap: 16px; /* Spaces out your cards */
  
  /* width: 50%; */
  /* background: #000; */
}

.task-list { display: flex; flex-direction: column; gap: 16px; }


</style>