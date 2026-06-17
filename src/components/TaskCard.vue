<template>
    <BaseCard>
    <h3>{{ taskCard.title }}</h3>
    <p>
        Status:
        <span v-if="taskCard.completed">Complete</span>
        <span v-else>Pending</span>
    </p>
    <button @click="completeTask" :disabled="taskCard.completed" class="delete">Complete</button >
    <button @click="deleteTask" class="complete">Delete</button>
    
    </BaseCard>

</template>


<script setup>
import { defineProps } from 'vue';
import BaseCard from './BaseCard.vue';
const props=defineProps({
  taskCard: Object
});
const emit=defineEmits(["delete","complete"])

const deleteTask =()=>{
    // console.log(props.taskCard);
    emit('delete', props.taskCard.id)
} 

const completeTask =()=>{
    // console.log(props.taskCard);
    emit('complete',props.taskCard.id)
}
</script>
<style scoped>
button {
  padding: 8px 12px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-weight: 600;
  transition: 0.2s;
  margin: 10px;
}

.complete {
  background: #4f46e5;
  color: white;
}
.delete {
  background: #ef4444;
  color: white;
}

</style>



