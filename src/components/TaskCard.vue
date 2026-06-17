<template>
  <BaseCard>
    <div class="flex flex-col gap-2">
      <h1 class="text-2xl font-semibold text-blue-600">
        {{ props.taskTitle }}
      </h1>
      <div class="">
        <span class="text-gray-500 text-sm">Completed: </span>
        <span
          class="text-sm text-white px-2 py-1 rounded-sm transition ease-in-out duration-10"
          :class="
            props.com === 'Completed' ? 'bg-green-500' : 'bg-orange-500'
          "
        >
          {{ props.taskCompleted }}
        </span>
      </div>
    </div>
    <div class="flex gap-x-2">
      <BaseButton
        :label="'Complete'"
        :optionalStyle="'bg-blue-400 hover:bg-blue-600'"
        @click="handleComplete"
      />
      <BaseButton
        :label="'Delete'"
        :optionalStyle="'bg-red-400 hover:bg-red-600'"
        @click="handleDelete"
      />
    </div>
  </BaseCard>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
import BaseButton from "@/ui/BaseButton.vue";
import BaseCard from "@/ui/BaseCard.vue";

const props = defineProps({
  taskId: {
    type: Number,
    required: true,
  },
  taskTitle: {
    retuired: true,
    type: String,
  },
  taskCompleted: {
    required: true,
    type: Boolean,
  },
});

const emit = defineEmits(["complete", "delete"]);
const handleComplete = () => {
  emit("complete", props.taskId);
};

const handleDelete = () => {
  emit("delete", props.taskId);
};
</script>

<style lang="scss" scoped></style>
