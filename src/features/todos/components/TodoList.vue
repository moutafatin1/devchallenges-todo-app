<script lang="ts" setup>
import MyIcon from '@/components/elements/MyIcon.vue'
import type { Todo } from '@/views/HomeView.vue'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps<{
  todos: Todo[]
  deleteTodo: (id: number) => void
}>()

const route = useRoute()
const filteredTodos = computed(() => {
  if (route.query.filter === 'active') {
    return props.todos.filter((todo) => !todo.completed)
  }
  if (route.query.filter === 'completed') {
    return props.todos.filter((todo) => todo.completed)
  }
  return props.todos
})
</script>

<template>
  <ul class="space-y-2">
    <li class="flex items-center gap-4" v-for="todo in filteredTodos" :key="todo.id">
      <input
        type="checkbox"
        class="h-5 w-5 rounded-md text-primary focus:ring-primary"
        :checked="todo.completed"
      />
      <span class="text-lg font-medium text-gray-700">{{ todo.body }}</span>
      <button
        v-if="todo.completed"
        @click="deleteTodo(todo.id)"
        class="ml-auto inline-flex items-center rounded-md text-gray-500 transition hover:text-red-500 focus:outline-none focus:ring-1 focus:ring-red-500 focus:ring-offset-2"
      >
        <MyIcon icon="ic:twotone-delete-outline" class="text-2xl" />
      </button>
    </li>
  </ul>
</template>
