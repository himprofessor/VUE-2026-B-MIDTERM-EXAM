<template>
    <div>
            <div  class="task-list" v-if="tasks.length">

                <TaskCard  v-for="task in tasks"
                            :key="task.id"
                            :task="task"
                            @complete="emit('complete', $event)"
                            @delete="emit('delete', $event)"
              />

            </div>

            <div class="empty" v-else>

                <div class="title-nothing">No tasks!!</div>
                <div class="no-subtitle">Enjoy your free time! </div>
            </div>
    </div>

</template>

<script setup>


   import TaskCard from './TaskCard.vue';

defineProps({
    tasks: {
        type: Array,
        required : true,

    },

})

const emit = defineEmits(['complete' , 'delete'])



</script>

<style scoped>


.task-list{
    display: grid;
    gap: 12px;
    margin-top: 13px;
}

.empty{
    margin-top: 14px;
  padding: 20px;
  border: 1px solid gray;
  border-radius: 12px;
  background: gray;
  text-align: center;
}

.title-nothing{
     font-size: 18px;
    font-weight: 800;
    margin-bottom: 6px;
}

.no-subtitle{
 opacity: 1;
}


</style>