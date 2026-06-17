<template>
    <button :class="['px-4 py-2 font-semibold text-md text-white rounded-md', props.optionalStyle]"
    @click="handleClick">
        {{ props.label }}
    </button>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    label: {
        required: true,
        type: String,
        defualt: 'Button',
    },
    optionalStyle: {
        type: String,
        defualt: "",
    }
});

const emit = defineEmits(['click'])

const handleClick = () => {
    emit('click')
}
</script>

<style lang="scss" scoped>

</style>