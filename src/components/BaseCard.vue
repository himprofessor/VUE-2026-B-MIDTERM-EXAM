<template>
  <div class="base-card">
    <header v-if="$slots.header" class="card-header">
      <slot name="header" />
    </header>
    

    <main class="card-body">
      <slot />
    </main>
  </div>
</template>

<style scoped>
.base-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 12px;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}
.card-header {
  border-bottom: 1px solid #f0f0f0;
  padding-bottom: 8px;
  margin-bottom: 12px;
}
</style>
