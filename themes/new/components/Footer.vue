<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useTouyingConfig } from '../../../composables/useTouyingConfig'
import ProgressBar from './ProgressBar.vue'

const config = useTouyingConfig()
const { $nav } = useSlideContext()
const page = useNavigationCurrent()
const total = computed(() => $nav.value?.slides.length ?? 1)
const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
</script>

<template>
  <footer class="new-footer">
    <div class="new-footer-meta">
      <span>{{ frontmatter.footer || config.footer || 'NEW' }}</span>
      <span>{{ page }} / {{ total }}</span>
    </div>
    <ProgressBar />
  </footer>
</template>

<style scoped>
.new-footer {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;
  background: #ffffff;
  border-top: 1px solid var(--new-line);
}

.new-footer-meta {
  height: 34px;
  padding: 0 78px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: var(--new-muted);
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.035em;
}
</style>
