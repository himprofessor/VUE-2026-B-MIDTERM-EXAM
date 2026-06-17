<template>
    <div class="border-1 h-55 rounded-lg w-60 shadow-lg">
        <div v-if="$slots.header"  class="bg-blue-500 rounded-lg border-solid-blue text-center h-10 py-2">
            <slot name="header"></slot>
            
        </div>

        <div>
            <slot/>
        </div>

        <div v-if="$slots.footer">
            <slot name="footer"/>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>