<script setup>
import BaseCard from './BaseCard.vue';

defineProps({
  task: {
    type: Object,
    required: true
  }
});

const emit = defineEmits(['complete', 'delete']);
</script>

<template>
  <BaseCard>
    <template #header>
      <h3 :class="{ completed: task.isDone }">{{ task.title }}</h3>
    </template>

    <p>{{ task.description }}</p>
    
    <div class="actions-row">
      <span class="status-badge" :class="task.isDone ? 'done' : 'pending'">
        {{ task.isDone ? 'Completed' : 'Pending' }}
      </span>

      <div class="buttons">
        <button v-if="!task.isDone" class="btn-complete" @click="emit('complete', task.id)">
          Complete
        </button>
        <button class="btn-delete" @click="emit('delete', task.id)">
          Delete
        </button>
      </div>
    </div>
  </BaseCard>
</template>

<style scoped>
.actions-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 15px;
}
.buttons {
  display: flex;
  gap: 8px;
}
button {
  border: none;
  padding: 4px 10px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
.btn-complete {
  background-color: #74b9ff;
  color: white;
}
.btn-delete {
  background-color: #ff7675;
  color: white;
}
h3 {
  margin: 0;
  color: #2c3e50;
}
.completed {
  text-decoration: line-through;
  color: #95a5a6;
}
.status-badge {
  display: inline-block;
  font-size: 0.8rem;
  padding: 4px 8px;
  border-radius: 4px;
  font-weight: bold;
}
.pending {
  background-color: #ffeaa7;
  color: #d63031;
}
.done {
  background-color: #55efc4;
  color: #00b894;
}
</style>
