<script setup lang="ts">
/**
 * Thin institutional progress line.
 */
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'

const { slides } = useNav()
const page = useNavigationCurrent()

const pct = computed(() => {
  const total = slides.value?.length ?? 1
  return Math.min((page.value / total) * 100, 100)
})
</script>

<template>
  <div class="uni-progress-bar">
    <div class="uni-progress-fill" :style="{ width: pct + '%' }" />
  </div>
</template>

<style scoped>
.uni-progress-bar {
  width: 100%;
  height: 5px;
  background: #eee7de;
  position: relative;
  flex-shrink: 0;
}

.uni-progress-fill {
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  background: var(--slidev-theme-primary);
  transition: width 0.3s ease;
}
</style>
