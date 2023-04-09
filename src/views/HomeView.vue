<script setup lang="ts">
import AddTodoForm from '@/features/todos/components/AddTodoForm.vue'
import StatusTab from '@/features/todos/components/StatusTab.vue'
import TodoList from '@/features/todos/components/TodoList.vue'
import { ref } from 'vue'

export type Todo = {
  id: number
  body: string
  completed: boolean
}

const todos = ref<Todo[]>([
  {
    id: 1,
    body: 'This is a todo',
    completed: false
  },
  {
    id: 2,
    body: 'This is an another todo',
    completed: true
  }
])

const addNewTodo = (body: string) => {
  const newTodo: Todo = {
    id: todos.value.length + 1,
    body,
    completed: false
  }

  todos.value.push(newTodo)
}

const deleteTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

const deleteCompleted = () => {
  todos.value = todos.value.filter((todo) => !todo.completed)
}
</script>

<template>
  <main class="mx-auto flex max-w-lg flex-col gap-4">
    <h1 class="my-8 text-center text-5xl font-bold text-gray-700">#todo</h1>
    <StatusTab />
    <AddTodoForm :addNewTodo="addNewTodo" />
    <TodoList :todos="todos" :deleteTodo="deleteTodo" :deleteCompleted="deleteCompleted" />
  </main>
</template>
