<script lang="ts" setup>
import { MyButton } from '@/components/elements'
import InputField from '@/components/forms/InputField.vue'
import { toTypedSchema } from '@vee-validate/zod'
import { useForm } from 'vee-validate'
import { z } from 'zod'

const props = defineProps<{
  addNewTodo: (body: string) => void
}>()
const { handleSubmit, handleReset } = useForm({
  validationSchema: toTypedSchema(
    z.object({
      todo: z.string().min(1, 'Must not be empty')
    })
  )
})

const addNewTodo = handleSubmit((data) => {
  props.addNewTodo(data.todo)
  handleReset()
})
</script>
<template>
  <form class="flex items-center gap-8" @submit="addNewTodo">
    <InputField name="todo" placeholder="Add new todo" class="focus:ring-primary" />
    <MyButton class="ml-auto bg-blue-500 px-6 hover:bg-blue-600">Add</MyButton>
  </form>
</template>
