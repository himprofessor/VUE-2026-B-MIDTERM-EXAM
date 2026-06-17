<template>
  <div>
    <TaskCard v-for="task in tasks" :key="task.id" :task="task"></TaskCard>
  </div>
</template>

<script setup>
import TaskCard from "./TaskCard.vue";
import { defineProps } from "vue";
const props = defineProps({
  tasks: {
    type: Object,
    require: true,
  },
});
</script>

<style lang="scss" scoped>
</style>