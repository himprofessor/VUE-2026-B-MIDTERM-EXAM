<template>
  <BaseCard>
    <template v-slot:header>
      <div class="card-title">
        <h3>{{ task.title }}</h3>
        <span v-if="task.completed" class="done-check">✅ Done</span>
      </div>
    </template>

    <template v-slot:default>
      <p>
        Status:
        <span :style="{ color: task.completed ? 'green' : 'orange' }">
          {{ task.completed ? "Completed" : "Pending" }}
        </span>
      </p>
    </template>

    <template v-slot:actions >
      <button @click="emit('complete', task.id)" class="btn btn-primary">Complete</button>
      <button @click="emit('delete', task.id)" class="btn btn-danger">Delete</button>
    </template>
  </BaseCard>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
import BaseCard from "./BaseCard.vue";

const props = defineProps({
  task: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["complete", "delete"]);

</script>

<style scoped>

.task-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.btn {
  margin-right: 8px;
  padding: 8px 16px;
  border-radius: 4px;
  border-radius: 4px;
  cursor: pointer;
  border: none;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
}

.btn-primary:hover {
  background-color: #0069d9;
}

.btn-danger {
  background-color: #dc3545;
  color: #fff;
}

.btn-danger:hover {
  background-color: #c82333;
}

.card-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-title h3 {
  font-weight: bold;
}

.done-check {
  color: green;
}

</style>
