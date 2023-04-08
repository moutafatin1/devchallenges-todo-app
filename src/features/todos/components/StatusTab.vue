<script lang="ts" setup>
import TabLink from './TabLink.vue'
</script>
<template>
  <div
    class="mx-auto flex max-w-lg items-center justify-around border-b-2 border-gray-300 pb-2 font-medium text-gray-600"
  >
    <TabLink filter="all">All</TabLink>
    <TabLink filter="active"> Active</TabLink>
    <TabLink filter="completed">Completed</TabLink>
  </div>
</template>
