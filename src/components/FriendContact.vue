<script setup>
import { ref } from 'vue'
const detailsAreVisible = ref(false)
const props = defineProps({
  id: {
    type: String,
    required: true
  },
  name: {
    type: String,
    required: true
  },
  phoneNumber: {
    type: String,
    required: true
  },
  emailAddress: {
    type: String,
    required: true
  },
  isFavorite: {
    type: Boolean,
    required: false,
    default: false
  }
})

const emit = defineEmits(['toggle-favorite', 'delete-friend'])

const toggleDetails = () => (detailsAreVisible.value = !detailsAreVisible.value)
const toggleFavorite = () => emit('toggle-favorite', props.id)
const deleteFriend = () => emit('delete-friend', props.id)
</script>

<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="deleteFriend">Delete</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<style scoped></style>
