<script setup lang="ts">
import { object, string, type InferType } from 'yup'
import type { FormSubmitEvent } from '#ui/types'

const schema = object({
  email: string().email('Invalid email').required('Required'),
  password: string()
    .min(8, 'Must be at least 8 characters')
    .required('Required')
})

type Schema = InferType<typeof schema>

const state = reactive({
  email: undefined,
  password: undefined
})

async function onSubmit(event: FormSubmitEvent<Schema>) {
  // Do something with event.data
  console.log(event.data)
}
</script>

<template>
  <div class="flex justify-center items-center w-screen h-screen">
    <UCard class="w-72 lg:w-96 m-auto">
      <UForm :schema="schema" :state="state" class="flex gap-2 flex-col" @submit="onSubmit">
        <h1 class="text-center">LOGIN</h1>
        <UFormGroup label="Email" name="email">
          <UInput placeholder="you@example.com" icon="i-heroicons-envelope" v-model="state.email" />
        </UFormGroup>

        <UFormGroup label="Password" name="password">
          <UInput placeholder="Enter password" icon="i-heroicons-key" v-model="state.password" type="password" />
        </UFormGroup>

        <div class="flex flex-row-reverse justify-between items-center mt-4">
          <UButton type="submit" icon="i-heroicons-arrow-right-end-on-rectangle-16-solid" size="sm" color="primary"
            variant="solid" label="Sign In" />

          <UButton type="button" to="/blog/register" icon="i-heroicons-bolt" size="sm" color="gray" variant="solid"
            label="Register" />
        </div>
      </UForm>
    </UCard>
  </div>
</template>