<template>
    <div>
        <input type="text" :placeholder="props.placeholder" class="px-4 py-2 rounded-md " >
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    placeholder: {
        type: String,
    },
})


</script>

<style lang="scss" scoped>

</style>