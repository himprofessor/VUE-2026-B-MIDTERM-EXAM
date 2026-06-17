<template>
    <div v-for="task in props.tasks" :key="task.id" class="flex flex-col items-center">
        <TaskCard :task="task" @complete="$emit('complete', $event)" @delete="$emit('delete', $event)"></TaskCard>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

import TaskCard from './TaskCard.vue';

const props = defineProps({
    tasks: Array,
    require: true
})

const emit = defineEmits({
    'complete': (taskId) => true,
    'delete': (taskId) => true,
});
</script>