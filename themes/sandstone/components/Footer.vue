<script setup lang="ts">
/**
 * Sandstone footer: white field, quiet metadata, strong page marker.
 */
import { useNav, useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'

const { slides } = useNav()
const { $nav } = useSlideContext()
const page = useNavigationCurrent()

const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
const first = computed(() => slides.value[0].meta.slide.frontmatter ?? {})
const author = computed(() => frontmatter.value.footer?.[0] || first.value.author || '')
const title = computed(() => frontmatter.value.footer?.[1] || first.value.title || '')
const date = computed(() => first.value.date || '')
const total = computed(() => slides.value?.length ?? 1)
</script>

<template>
  <footer class="uni-footer">
    <div class="uni-footer-a">{{ author }}</div>
    <div class="uni-footer-b">{{ title }}</div>
    <div class="uni-footer-c">
      <template v-if="frontmatter.footer?.[2]">{{ frontmatter.footer[2] }}</template>
      <template v-else><span v-if="date">{{ date }} · </span>{{ page }} / {{ total }}</template>
    </div>
  </footer>
</template>

<style scoped>
.uni-footer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  display: grid;
  grid-template-columns: 25% 1fr 18%;
  height: 48px;
  font-size: 12px;
  z-index: 10;
  background: #ffffff;
  border-top: 1px solid var(--sandstone-line);
}

.uni-footer-a,
.uni-footer-b,
.uni-footer-c {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 0 22px;
  color: var(--sandstone-muted);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.uni-footer-a {
  color: var(--slidev-theme-secondary);
  font-weight: 700;
  padding-left: 72px;
}

.uni-footer-b {
  border-left: 1px solid var(--sandstone-line);
}

.uni-footer-c {
  justify-content: center;
  color: #ffffff;
  background: var(--slidev-theme-primary);
  font-weight: 720;
  letter-spacing: 0.04em;
}
</style>
