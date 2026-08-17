<script setup lang="ts">
/**
 * Sandstone editorial header.
 */
import TitleRenderer from '#slidev/title-renderer'
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useCurrentSectionSlideNo } from '../../../composables/useSlideStructure'
import ProgressBar from './ProgressBar.vue'

const { slides } = useNav()
const page = useNavigationCurrent()
const currentSectionSlideNo = useCurrentSectionSlideNo()

const logo = computed(() => slides.value[0].meta.slide.frontmatter.logo ?? '')
</script>

<template>
  <header class="uni-header">
    <ProgressBar />
    <div class="uni-header-row">
      <span class="uni-header-left">
        <TitleRenderer class="tou-title" :no="page" />
      </span>
      <span class="uni-header-right">
        <span class="uni-header-section">
          <TitleRenderer class="tou-title" :no="currentSectionSlideNo" />
        </span>
        <img v-if="logo" :src="logo" class="uni-header-logo" />
      </span>
    </div>
  </header>
</template>

<style scoped>
.uni-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  flex-direction: column;
  background: rgba(255, 255, 255, 0.97);
  z-index: 10;

  .uni-header-row {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    padding: 18px 72px 15px;
    gap: 24px;
    border-bottom: 1px solid var(--sandstone-line);
  }

  .uni-header-left {
    min-width: 0;
    max-width: calc(100% - 210px);
    font-size: 26px;
    font-weight: 700;
    color: var(--sandstone-ink);
    letter-spacing: -0.035em;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .uni-header-right {
    font-size: 12px;
    color: var(--slidev-theme-secondary);
    display: flex;
    align-items: center;
    gap: 12px;
    flex-shrink: 0;
    font-weight: 720;
    letter-spacing: 0.11em;
    text-transform: uppercase;
  }

  .uni-header-section {
    opacity: 0.78;
  }

  .uni-header-logo {
    height: 28px;
    width: auto;
    object-fit: contain;
  }
}
</style>
