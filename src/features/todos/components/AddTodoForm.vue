<script lang="ts" setup>
import { MyButton } from '@/components/elements'
import InputField from '@/components/forms/InputField.vue'
import { useForm } from 'vee-validate';
import {toTypedSchema} from "@vee-validate/zod"
import {z} from "zod"
const {handleSubmit,handleReset} = useForm({
    validationSchema : toTypedSchema(z.object({
        todo: z.string().min(1,"Must not be empty")
    }))
})

const addNewTodo = handleSubmit(data => {
    console.log(data)
    handleReset()
})
</script>
<template>
  <form class="flex items-center gap-8" @submit="addNewTodo">
    <InputField name="todo" placeholder="Add new todo" class="focus:ring-primary" />
    <MyButton class="ml-auto bg-primary px-6 hover:bg-primary/75">Add</MyButton>
  </form>
</template>
