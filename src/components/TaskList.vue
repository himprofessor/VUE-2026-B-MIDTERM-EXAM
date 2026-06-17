<template>
    <div class="task-list">
        <TaskCard
            v-for="item in tasks"
            :key="item.id"
            :student="item"
            @done="$emit('done', $event)"
            @complete="$emit('complete', $event)"
            @delete="$emit('delete',$event)"
        
        />
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import TaskCard from '@/components/TaskCard.vue';



defineProps({
    tasks:{
        type: Array,
        required: true
    }
})
defineEmits(['complete', 'delete', 'done']);

</script>

<style scoped>
.task-list{
    display: flex;
    flex-wrap: wrap;
}
</style>
