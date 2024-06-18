<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="email">Email:</label>
        <UInput id="email" v-model="email" type="email" />
      </div>
      <div>
        <label for="password">Password:</label>
        <UInput id="password" v-model="password" type="password" />
      </div>
      <div>
        <UButton type="submit">Login</UButton>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')

const handleSubmit = () => {
  // Handle form submission logic here
  console.log(`Email: ${email.value}, Password: ${password.value}`)
}
</script>