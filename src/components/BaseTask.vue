<template>
  <div class="base-card">
    <TaskCard>
      <slot></slot>
    </TaskCard>
    
  </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';
</script>

<style scoped>
.base-card {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 80%;
  height: 40vh;
  background: black;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 16px;
  margin-bottom: 1px;
}
</style>
