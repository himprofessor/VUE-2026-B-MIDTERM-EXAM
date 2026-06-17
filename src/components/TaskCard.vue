<template>
  <div class="border border-gray-300 rounded-md p-4 mb-4 bg-gray-50">
    <div class="flex justify-between items-center mb-2">
      <h3 class="font-medium text-gray-900">{{ task.title }}</h3>
      <span v-if="task.completed" class="text-green-600 font-bold text-sm">Done</span>
    </div>
    
    <div class="text-sm text-gray-700 mb-3 flex items-center gap-1">
      Status: 
      <span :class="task.completed ? 'text-green-500' : 'text-amber-500'">
        {{ task.completed ? '✅ Completed' : '⏳ Pending' }}
      </span>
    </div>
    

    <div class="flex justify-end gap-2">
      <button 
        @click="$emit('complete', task.id)" 
        :disabled="task.completed"
        class="border border-green-500 px-3 py-1 rounded text-sm hover:bg-green-500 hover:text-white transition">
    Complete
      </button>
      <button 
        @click="$emit('delete', task.id)" 
        class="border border-red-500 px-3 py-1 rounded text-sm hover:bg-red-500 hover:text-white transition">
     Delete
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  task: {
    type: Object,
    required: true
  }
});

defineEmits(['complete', 'delete']);
</script>

