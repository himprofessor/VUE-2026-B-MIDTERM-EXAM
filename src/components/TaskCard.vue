<template>
  <BaseCard>
    <h2>{{ tasks.title }}</h2>

    <p class="status">
      Status: <span>{{ tasks.completed ? "Completed" : "Pending" }}</span>
    </p>
    <div class="taskButton" style="padding: 10px; display: flex; gap: 10px">
      <button
        @click="$emit('complete', tasks.id)"
        style="
          padding: 10px;
          border-radius: 10px;
          background-color: green;
          color: white;
          cursor: pointer;
        "
      >
        Complete
      </button>
      <button
        @click="$emit('delete', tasks.id)"
        style="
          padding: 10px;
          border-radius: 10px;
          background-color: red;
          color: white;
          cursor: pointer;
        "
      >
        Delete
      </button>
    </div>
  </BaseCard>
</template>

<script setup>
import BaseCard from "./BaseCard.vue";
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  tasks: {
    type: Object,
    required: true,
  }
});

defineEmits(["complete", "delete"]);
</script>

<style lang="scss" scoped>
</style>