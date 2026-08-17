<script setup lang="ts">
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'

const { slides } = useNav()
const page = useNavigationCurrent()
const progress = computed(() => {
  const total = slides.value?.length ?? 1
  return Math.min((page.value / total) * 100, 100)
})
</script>

<template>
  <div class="new-progress" aria-hidden="true">
    <div class="new-progress-fill" :style="{ width: `${progress}%` }" />
  </div>
</template>

<style scoped>
.new-progress {
  position: relative;
  width: 100%;
  height: 5px;
  overflow: hidden;
  background: var(--new-track);
}

.new-progress-fill {
  position: absolute;
  inset: 0 auto 0 0;
  height: 100%;
  background: var(--slidev-theme-primary);
  transition: width 0.28s ease;
}
</style>
