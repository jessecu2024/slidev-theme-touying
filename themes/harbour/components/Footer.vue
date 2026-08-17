<script setup lang="ts">
/**
 * TouFooter
 *
 * Quiet footer with a blue page indicator.
 * - Left: custom text (e.g. author name) via touying.footer
 * - Right: page counter (or custom text) via touying.footerRight
 */
import { useNav } from '@slidev/client'
import { useSlideContext } from '@slidev/client'
import { useTouyingConfig } from '../../../composables/useTouyingConfig'
import { computed } from 'vue'

const config = useTouyingConfig()
const { total } = useNav()
const { $nav } = useSlideContext()
const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
</script>

<template>
  <footer class="dew-footer">
    <span class="dew-footer-left">{{ frontmatter.footer || config.footer || $nav.slides[0].meta.slide.frontmatter.footer }}</span>
    <span class="dew-footer-right">
      <template v-if="config.footerRight">{{ config.footerRight }}</template>
      <template v-else>{{ $nav.currentPage }} / {{ total }}</template>
    </span>
  </footer>
</template>

<style scoped>
.dew-footer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 74px 17px;
  font-size: 12px;
  color: var(--harbour-muted);
  box-sizing: border-box;
}

.dew-footer-left {
  letter-spacing: 0.025em;
}

.dew-footer-right {
  color: var(--slidev-theme-primary);
  font-weight: 750;
  letter-spacing: 0.06em;
}
</style>
