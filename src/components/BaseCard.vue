<script setup>
</script>

<template>
  <div class="base-card">
   
    <slot></slot>
  </div>
</template>
<style scoped>
.base-card {
  background-color: #f1f2f3;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05), 0 1px 3px rgba(0, 0, 0, 0.1);
  padding: 16px;
  margin-bottom: 12px;
  border: 1px solid #e2e8f0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.base-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(254, 246, 246, 0.08);
}
</style>
