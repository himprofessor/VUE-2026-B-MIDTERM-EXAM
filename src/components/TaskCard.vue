<script setup>
import BaseCard from './BaseCard.vue'

const props = defineProps({
  student: {
    type: Object,
    required: true,
  },
})
const emit = defineEmits(['view-detail', 'delete'])

const handleViewDetail = () => emit('view-detail', props.student.id)
const handleDelete = () => emit('delete', props.student.id)
</script>