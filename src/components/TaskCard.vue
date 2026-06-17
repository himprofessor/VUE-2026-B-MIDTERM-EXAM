<template>
  <BaseCard>
    <div class="task-card">
      <div class="info">
        <h3>{{ task.title }}</h3>
        <div class="actions">
          <button class="delete" @click="deleteTask">Delete</button>
          <button class="Completed" @click="completedTask">Complete</button>
        </div>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'
import BaseCard from './BaseCard.vue'

const props = defineProps({
  task: { type: Object, required: true },
})

const emit = defineEmits([ 'delete', 'Completed'])

function completedTask() {
  const current = props.task
  const completed = window.prompt('Task completed', current.completed)
  if (completed === true) return 
  else (current.completed = false) 
  emit('Completed', props.task)
}

function deleteTask() {
  emit('delete', props.task.id)
}

</script>

<style scoped>
.task-card {
  display: flex;
  gap: 12px;
  flex-direction: column;
  align-items: center;
  width: 100%;
  text-align: center;

}
.info h3 {
  margin: 0;
  font-size: 16px;
}
.actions {
  margin-top: 8px;
}
.actions button {
  margin-right: 8px;
}

.actions .Completed {
  background: #09c959;
  color: #fff;
  border: 2px solid #2fbc65;
  border-radius: 5px;
}
.actions .panding {
  background: #109dd0;
  color: #fff;
  border: 2px solid #007bff;
  border-radius: 5px;
}

.actions .delete {
  background: red;
  color: #fff;
  border: 2px solid red;
  border-radius: 5px;
}
</style>
 
