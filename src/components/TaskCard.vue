<template>
  <div class="task-card" :class="{ completed: task.completed }">
    <div class="task-info">
      <h3>{{ task.title }}</h3>
      <span :class="['status', task.completed ? 'status-completed' : 'status-pending']">
        {{ task.completed ? 'Completed' : 'Pending' }}
      </span>
    </div>

    <div class="task-actions">
      <button
        :class="['btn', task.completed ? 'btn-pending' : 'btn-complete']"
        @click="$emit('completeTask', task)"
      >
        {{ task.completed ? 'Mark Pending' : 'Complete' }}
      </button>

      <button class="btn btn-view" @click="$emit('viewTaskDetails', task)">View Detail</button>
      <button class="btn btn-delete" @click="$emit('deleteTask', task)">Delete</button>
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

defineEmits(["viewTaskDetails", "completeTask", "deleteTask"]);
</script>

<style scoped>
.task-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: teal;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  border: 1px solid #eef2f5;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  margin-bottom: 16px;
}

.task-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
}

.task-card.completed {
  border-left: 5px solid #2ecc71;
  background-color: #84ebeb;
}

.task-card.completed h3 {
  text-decoration: line-through;
  color: #7f8c8d;
}

.task-info h3 {
  margin: 0 0 12px 0;
  font-size: 1.2rem;
  color: white;
}

.status {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
}

.status-pending {
  background-color: #ffeaa7;
  color: rgb(201, 13, 13);
}

.status-completed {
  background-color: #d4edda;
  color: #155724;
}

.task-actions {
  display: flex;
  gap: 8px;
  margin-top: 16px;
  flex-wrap: wrap;
}

.btn {
  flex: 1;
  min-width: 80px;
  padding: 8px 12px;
  border: none;
  border-radius: 6px;
  font-weight: 600;
  font-size: 0.85rem;
  cursor: pointer;
  transition: background 0.2s ease, color 0.2s ease;
}

.btn-complete {
  background-color: #2ecc71;
  color: white;
}
.btn-complete:hover { background-color: #27ae60; }

.btn-pending {
  background-color: #f1f2f6;
  color: #2c3e50;
}
.btn-pending:hover { background-color: #dfe4ea; }

.btn-view {
  background-color: #3498db;
  color: white;
}
.btn-view:hover { background-color: #2980b9; }

.btn-delete {
  background-color: #ce2513;
  color: white;
}
.btn-delete:hover { background-color: rgb(216, 21, 21); }
</style>
