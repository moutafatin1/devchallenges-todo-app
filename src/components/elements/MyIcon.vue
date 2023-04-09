<script lang="ts" setup>
interface Props {
  icon: string
}
defineProps<Props>()
</script>

<template>
  <iconify-icon :icon="icon" class="inline-flex items-center justify-center text-xl"></iconify-icon>
</template>
