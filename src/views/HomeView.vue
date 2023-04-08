<script setup lang="ts">
import AddTodoForm from '@/features/todos/components/AddTodoForm.vue'
import StatusTab from '@/features/todos/components/StatusTab.vue'
</script>

<template>
  <main class="mx-auto flex max-w-lg flex-col gap-4">
    <h1 class="my-8 text-center text-5xl font-bold text-gray-700">#todo</h1>
    <StatusTab />
    <AddTodoForm />
  </main>
</template>
