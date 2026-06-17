<template>
  <div class="border-2 border-blue-500 rounded-lg bg-white shadow-md overflow-hidden max-w-md mx-auto my-6">
    <div v-if="$slots.header" class="bg-gray-100 p-4 border-b-2 border-teal-500">
      <slot name="header"></slot>
    </div>
    
    <div class="p-4 bg-teal-50">
      <slot></slot>
    </div>
  </div>
</template>
