<template>
  <BaseCard>
    <div>
      <div>
        <h4 :class="{ computed: task.completed }">
          {{ task.title }}
        </h4>
        <span v-if="task.completed">Done</span>
      </div>
      <p>Startus:<span :class="task.completed ? 'text-completed' : 'text-pending'">{{task.completed ? "competed" : "pending"}}</span></p>
      <div>
        <button v-if="!task.completed" @click="emit('complete', task.id)">
          complete
        </button>
        <button  @click="emit('delete', task.id)">delete</button>
      </div>
    </div>
  </BaseCard>
</template>

<script setup>
import { computed } from "vue";

defineProps({
  task: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["complete", "delete"]);
</script>

<style lang="scss" scoped></style>
