<template>
    <BaseCard>
        <div class="flex d-flex justify-between">
            <h3 class="text-lg font-semibold text-gray-800">{{ props.task.title }}</h3>
            <p v-if="props.task.completed" class="p-1 text-green-600 font-bold">Done</p>
        </div>
        <p v-if="props.task.completed">Status: Complete</p>
        <p v-else>Status: Pending</p>
        <div class="flex d-flex gap-4 mt-2">
            <button @click="handleComplete" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded-lg transition-colors duration-200">Complete</button>
            <button @click="handleDelete" class="flex-1 bg-red-600 hover:bg-red-700 text-white font-semibold py-2 px-4 rounded-lg transition-colors duration-200">Delete</button>
        </div>
    </BaseCard>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

import BaseCard from './BaseCard.vue';

const props = defineProps({
    task: Object,
    require: true
})

const emit = defineEmits({
    'complete': (taskId) => true,
    'delete': (taskId) => true,
});

const handleComplete = () => {
    emit('complete', props.task.id);
};

const handleDelete = () => {
    emit('delete', props.task.id);
};

</script>