<template>
  <div class="card">
    <div v-if="$slots.header" class="card-header">
      <slot name="header"></slot>
    </div>
    
    <div class="card-body">
      <slot></slot>
    </div>
    
    <div v-if="$slots.actions" class="card-button">
      <slot name="actions"></slot>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>

.card {
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 16px;
  padding: 16px;
  background-color: #fff;
}

.card:hover {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  /* transform: scale(1.02); */
}

.card-header {
  font-weight: bold;
  margin-bottom: 8px;
}

.card-body {
  margin-bottom: 8px;
}

.card-button {
  display: flex;
  justify-content: flex-end;
  gap: 4px;
}

</style>
