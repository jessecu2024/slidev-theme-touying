<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(defineProps<{
  color?: 'ochre' | 'blue' | 'red' | 'gray'
}>(), {
  color: 'ochre',
})

const className = computed(() => `hl-${props.color}`)
</script>

<template>
  <span :class="className"><slot /></span>
</template>
