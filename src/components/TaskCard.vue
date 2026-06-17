<template>
    <div>
        <h2>My Tasks</h2>
        <p>I have {{ tasks.length }} tasks to complete</p>
        <BaseCard>
            <div class="tasks-card-content">
                <p>{{ tasks.title }}</p>
                <button @click="$emit('done', tasks.id)">Done</button>
                <p><strong>Complete:</strong> {{ tasks.completed }}</p>
                <div>
                    <button @click="$emit('complete', tasks.id)">complete</button>
                    <button class="btn-delete" @click="$emit('delete', tasks.id)">delete</button>
                </div>
            </div>
        
        </BaseCard>
    </div>
</template>

<script setup>
import { defineProps, defineEmits} from 'vue';
import BaseCard from '@/components/BaseCard.vue';

defineProps({
    tasks:{
        type:Object,
        required: true
    }
})
defineEmits(['complete', 'delete', 'done']);
</script>

<style scoped>

h2, p{
    margin-bottom: 10px;
    text-align: center;
}


.avatar{
    width: 80px;
    height: 80px;
    border-radius:50px;
}
.actions{
    margin-top: 10px;
    display: flex;
    gap: 10px;
}
button{
    padding: 6px 12px;
    cursor: pointer
}
.btn-delete{
    background-color: #ff4d4d;
    color: white;
    border: none;
    border-radius: 4px;
}
</style>
