<script lang="ts" setup>
import type { Todo } from '@/views/HomeView.vue'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps<{
  todos: Todo[]
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
    </li>
  </ul>
</template>
