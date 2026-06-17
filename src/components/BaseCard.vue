<template>
    <div class="base-card">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style  scoped>
.base-card {
  background-color: #ffffff;
  border-radius: 8px;
  padding: 16px 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: all 0.2s ease;
  border-left: 5px solid #bdc3c7; /* Default gray frame border */
}

.base-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

</style>