<template>
    
    
    <BaseCard>
            <div class="task-card">

                <h4 class="title"> {{ task.title }}</h4>

                <span class="status" :class="task.completed  ?   'completed': 'pending'">
                        {{ task.completed ? "Completed ": "Pending " }}
                </span>
        
                <div class="actions">
                    <button class="btn-complete" @click="emitComplete"> Complete</button>
                    <button class="btn-delete" @click="emitDelete"> Delete</button>

                </div>

         </div>

    </BaseCard>

</template>

<script setup>
    import BaseCard from './BaseCard.vue';

const emit =defineEmits(['complete', 'delete'])

const props = defineProps ({

    task: {
        type: Object,
        required: true,

    },

})


const emitComplete = () => emit('complete',   props.task.id)
const emitDelete = () => emit('delete',   props.task.id)


</script>

<style scoped>
.task-card{
    display: flex;
    flex-direction: column;
    gap:12px ;
}

.title{
    font-size: 16px;
    font-weight: 100px;
}

.actions{
   display: inline-flex;
  align-items: center;
  gap: 8px;
  font-weight: 600;
  padding: 6px 10px;
  border-radius: 999px;
  border: 1px solid rgba(178, 163, 163, 0.18);
  width: fit-content;
}
.pending{
    color: rgb(233, 231, 228);
    background: #f19c3b;
    padding: 12px;
      border-radius: 12px;
}

.completed{
    color: white;
    background: #134211;
    padding: 12px;
    border-radius: 12px;
}



.btn-complete {
  background: #c5b911;
  color: white;
   border: none;
  border-radius: 8px;
  padding: 8px 12px;
  cursor: pointer;
  font-weight: 600;
}

.btn-delete {
  background: #ef4444;
  color: white;
   border: none;
  border-radius: 8px;
  padding: 8px 12px;
  cursor: pointer;
  font-weight: 600;
}
</style>