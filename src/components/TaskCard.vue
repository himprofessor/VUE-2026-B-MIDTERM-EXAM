<script setup>
import BaseCard from './BaseCard.vue';

defineProps(['task']);

const emit = defineEmits(['complete-task', 'delete-task']);

</script>

<template>
    <BaseCard>
        <h3>{{ task.title }}</h3>
        <p>
            Status:
            <strong :style="{color: task.completed ? 'green' : 'orange'}">
                {{ task.completed ? 'Completed' : 'Pending'}}
            </strong>
       
        </p>
        <div class="buttons">
  <button
    v-if="!task.completed"
    class="complete-btn"
    @click="$emit('complete-task', task.id)"
  >
    Complete
  </button>

  <button
    class="delete-btn"
    @click="$emit('delete-task', task.id)"
  >
    Delete
  </button>
</div>
    </BaseCard>
</template>

<style scoped>
h3 {
  margin-bottom: 15px;
}

.buttons {
  margin-top: 15px;
}
.complete-btn,
.delete-btn {
  border: none;
  padding: 10px 16px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}

.complete-btn {
  background-color: #28a745;
  margin-right: 10px;
}

.delete-btn {
  background-color: #dc3545;
}

.complete-btn:hover {
  background-color: #218838;
}

.delete-btn:hover {
  background-color: #c82333;
}

.completed {
  color: green;
  font-weight: bold;
}

.pending {
  color: orange;
  font-weight: bold;
}
</style>