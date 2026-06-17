<script setup>
import TaskCard from './TaskCard.vue';

defineProps(['tasks']);
defineEmits(['complete-task', 'delete-task']);
</script>

<template>
    <div>
        <div v-if="tasks.length >0">
            <TaskCard
            v-for="task in tasks"
            :key="task.id"
            :task="task"
            @complete-task="$emit('complete-task',$event)"
            @delete-task="$emit('delete-task',$event)"
            />
        </div>
        <div v-else class="empty-state">
           <h2>No tasks left!</h2>
           <p> Enjoy your free time.</p>
        </div>
    </div>
</template>
<style scoped>
.empty-state{
    text-align:center;
    padding:30px;
    background-color: white;
    border-radius:8px;
}
</style>