<template>
    <div v-if="props.tasks.length > 0" class="flex flex-col gap-4">
        <TaskCard v-for="task in props.tasks" 
        :key="task.id"
        :task-id="task.id"
        :task-title="task.title"
        :task-completed="task.completed"
        @complete="handleComplete"
        @delete="handleDelete" />
    </div>
    <EmptyStat v-else />
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import TaskCard from './TaskCard.vue';
import EmptyStat from './EmptyStat.vue';

const props = defineProps({
    tasks: {
        type: Array,
        required: true
    },
})

const emit = defineEmits(['markComplete', 'deleteTask'])
const handleComplete = (taskId) => {
    emit('markComplete',taskId)
};

const handleDelete = (taskId) => {
    emit('deleteTask',taskId)
};
</script>

<style lang="scss" scoped>

</style>