<template>
  <div class="base-card">
    <slot></slot>
  </div>
</template>

<style scoped>
.base-card {
  border: 1px solid #ccc;
  padding: 12px;
  margin: 12px 0;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}
</style>