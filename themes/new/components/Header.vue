<script setup lang="ts">
import TitleRenderer from '#slidev/title-renderer'
import { useCurrentSectionSlideNo } from '../../../composables/useSlideStructure'

const currentSectionSlideNo = useCurrentSectionSlideNo()
</script>

<template>
  <header class="new-header">
    <span class="new-header-section">
      <TitleRenderer class="tou-title" :no="currentSectionSlideNo" />
    </span>
    <span class="new-header-mark">NEW</span>
  </header>
</template>

<style scoped>
.new-header {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  padding: 24px 78px 0;
  color: var(--new-muted);
  font-size: 12px;
  font-weight: 650;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.new-header-section {
  max-width: 70%;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.new-header-mark {
  color: var(--slidev-theme-primary);
  letter-spacing: 0.16em;
}
</style>
