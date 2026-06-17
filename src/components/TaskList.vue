<template>
    <div>
        <div v-if="tasks.length===0" >
            <h3 style="color: lightcoral; background: pink; padding: 25px 30px; width: 300px; border-radius: 20px;">
             ! No tasks Enjoy your free time
           </h3>
        </div>
        <div v-else>
            <TaskCard
                v-for="task in tasks" 
                :key="task.id" 
                :taskCard="task"
                @delete="emitDelete"
                @complete="emitComplete"
        />
        </div>
    </div>
</template>

<script setup>
import TaskCard from './TaskCard.vue';

defineProps({
  tasks: Array
});
const emit=defineEmits(["delete-task","complete-task"]) 

const emitDelete =(id)=>{
    emit ('delete-task',id)
}

const emitComplete=(id)=>{
    emit('complete-task',id)
}
</script>
<style scoped>

</style>



