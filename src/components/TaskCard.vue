
<template >
  <BaseCard>
        <template #header>
        <div>
            {{ task.title }}
        </div>
        </template>

        <div>
        <h1 class="text-center">Status</h1>
        <div class="flex gap-12 ml-6 mt-6">
          <span class="text-red-500">Pending</span>
          <span class="text-blue-500">Complete</span>
        </div>
        
        </div>

        <template #footer>
            <div class="flex gap-4 px-5">
                <div class="w-20 text-center rounded-lg bg-green-300 py-1 border-1 mt-12 ">
                    <button @click="onComplete">
                    Complete
                    </button>
                </div>

                <div class="border-1 w-20 text-center rounded-lg bg-red-600 mt-12  ">
                    <button @click="onDelete">
                    Delete
                    </button>
                </div>
            </div>
        </template>
  </BaseCard>
</template>

<script setup>
import BaseCard from './BaseCard.vue'

const props = defineProps({
  task: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['complete', 'delete'])

function onComplete() {
  emit('complete', props.task)
}

function onDelete() {
  emit('delete', props.task.id)
}
</script>