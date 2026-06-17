<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style scoped>
.card {
  position: relative;
  padding: 18px;
  margin: 20px 30px;
  border-radius: 20px;

  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(59, 236, 236, 0.3);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
  transition: all 0.3s ease;
  overflow: hidden;
}
.card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  height: 5px;
  width: 100%;
  background: linear-gradient(90deg, #3b82f6);
  opacity: 0.9;
}
.card:hover {
  transform: translateY(-6px) scale(1.01);
  box-shadow: 0 14px 30px rgba(0, 0, 0, 0.12);
}
</style>
