<script setup>
import { ref } from 'vue'
const emit = defineEmits(['add-contact'])
const enteredName = ref('')
const enteredPhone = ref('')
const enteredEmail = ref('')

const submitData = () => {
  emit('add-contact', enteredName, enteredPhone, enteredEmail)
}
</script>

<template>
  <form @submit.prevent="submitData">
    <div>
      <label for="">Name</label>
      <input type="text" name="" id="" v-model="enteredName" />
    </div>
    <div>
      <label for="">Phone</label>
      <input type="tel" name="" id="" v-model="enteredPhone" />
    </div>
    <div>
      <label for="">E-mail</label>
      <input type="email" name="" id="" v-model="enteredEmail" />
    </div>
    <div><button>Add Contact</button></div>
  </form>
</template>

<style scoped></style>
