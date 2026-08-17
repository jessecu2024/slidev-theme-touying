<script setup lang="ts">
import TitleRenderer from '#slidev/title-renderer'
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useCurrentSectionSlideNo } from '../../../composables/useSlideStructure'
import { useTouyingConfig } from '../../../composables/useTouyingConfig'

const config = useTouyingConfig()
const { $nav } = useSlideContext()
const page = useNavigationCurrent()
const sectionNo = useCurrentSectionSlideNo()
const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
const total = computed(() => $nav.value?.slides.length ?? 1)
const left = computed(() => frontmatter.value.footer || config.value.footer)
const showSection = computed(() => config.value.sectionFooter && sectionNo.value > 1)
</script>

<template>
  <footer class="syd-footer">
    <span class="syd-footer-left">{{ left }}</span>
    <span v-if="showSection" class="syd-footer-section">
      <TitleRenderer class="tou-title" :no="sectionNo" />
    </span>
    <span class="syd-footer-page">{{ page }} / {{ total }}</span>
  </footer>
</template>

<style scoped>
.syd-footer {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: baseline;
  min-height: 34px;
  padding: 0 var(--slide-margin-x) 13px;
  color: var(--text-muted);
  font-size: 13px;
  line-height: 1;
  letter-spacing: 0.015em;
}

.syd-footer-left {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.syd-footer-section {
  max-width: 360px;
  overflow: hidden;
  color: var(--text-muted);
  text-overflow: ellipsis;
  white-space: nowrap;
}

.syd-footer-page {
  justify-self: end;
  font-variant-numeric: tabular-nums;
}
</style>
