<template>
  <BaseCard>
    <div class="card">
      <div>
        <span> {{ task.completed ? 'Completed' : 'Pending' }}</span>
      </div>
      <div class="buttoncard">
        <button class="complete" @click="$emit('complete', task.id)">  Complete</button>
        <button class="delate" @click="$emit('delete-task', task.id)">  Delete</button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
  import BaseCard from './BaseCard.vue';
  
  defineProps({
    task: Object
  });
  defineEmits(['complete', 'delete-task']);
</script>

<style scoped>
  .buttoncard{
    display: flex;
    gap:10px;
  }
  button{
    background-color: blue;
    color: white;
    padding: 5px 10px;
    border: 1px solid #ddd;
    margin: 10px 0px;
  }
  .delate{
    background-color: red;
  }
  .card {
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 10px;
    gap: 15px;
    margin-top: 20px;
  }

</style>