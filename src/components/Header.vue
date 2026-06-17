<template>
    <header class="px-4 py-2 w-full text-left">
        <h1 class="text-3xl text-blue-600 font-bold">
            My tasks
        </h1>
        <p v-if="haveTask" class="text-gray-600">
            You have {{ numberOfTask }} tasks today!
        </p>
        <p v-else class="text-gray-600">
            You don't have task for today
        </p>
    </header>
</template>

<script setup>
import { ref, watch, defineProps, computed } from 'vue';
const props = defineProps({
    numberOfTask : {
        required : true,
        type: Number
    }
})

const haveTask = computed(() => props.numberOfTask > 0);



</script>

<style lang="scss" scoped>

</style>