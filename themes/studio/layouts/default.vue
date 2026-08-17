<script setup lang="ts">
/**
 * Studio default slide.
 */
import { useNav } from '@slidev/client'
import { computed } from 'vue'

const { slides } = useNav()

const total = computed(() => slides.value?.length ?? 1)
</script>

<template>
  <div class="slidev-layout default">
    <slot />
  </div>
</template>

<style>
</style>
