<template>
  <div>
    <div v-if="tasks.length === 0" class="empty-state">
      <p>No tasks left!</p>
      <p>Enjoy your free time!have a nice days</p>
    </div>

    <TaskCard
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @complete-task="$emit('complete-task',$event)"
      @delete-task="$emit('delete-task', $event)"
    />
  </div>
</template>

<script setup>
import TaskCard from "./TaskCard.vue"

defineProps({ tasks: Array })
defineEmits(["complete-task", "delete-task"])
</script>


<style scoped>
.empty-state {
  text-align: center;
  padding: 48px 0;
  color: #6fbaf0;
  font-size: 40px;
}

.empty-state p {
  margin: 4px 0;
}
</style> 
