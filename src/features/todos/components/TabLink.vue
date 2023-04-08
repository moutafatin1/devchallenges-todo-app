<script lang="ts" setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps<{
  filter: string
}>()

const route = useRoute()
const isActive = computed(() => {
  if (!route.query.filter && props.filter === 'all') {
    return true
  }
  return route.query.filter === props.filter
})
</script>

<template>
  <RouterLink :to="`?filter=${filter}`" class="tab-link" :class="{ active: isActive }">
    <slot />
  </RouterLink>
</template>

<style scoped>
.tab-link {
  @apply relative inline-block;
}

.active {
  @apply after:absolute after:left-1/2 after:top-[1.8rem] after:w-24 after:-translate-x-1/2 after:rounded-t-lg after:border-b-4 after:border-primary;
}
</style>
