<template>
  <div class="base-card">
    <div v-if="$slots.header" class="card-header">
      <slot name="header" />
    </div>
    <div class="card-body">
      <slot />
    </div>
    <div v-if="$slots.actions" class="card-actions">
      <slot name="actions" />
    </div>
  </div>
</template>


<style scoped>
.base-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 12px;
  background: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}
.card-header {
  margin-bottom: 8px;
}
.card-header h3 {
  margin: 0;
}
.card-body {
  margin-bottom: 12px;
}
.card-actions {
  display: flex;
  gap: 8px;
}
</style>
