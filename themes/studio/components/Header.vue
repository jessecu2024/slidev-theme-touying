<script setup lang="ts">
import TitleRenderer from '#slidev/title-renderer'
import { useCurrentSectionSlideNo } from '../../../composables/useSlideStructure'

const currentSectionSlideNo = useCurrentSectionSlideNo()
</script>

<template>
  <header class="spl-header">
    <span class="spl-header-left">
      <TitleRenderer class="tou-title" :no="currentSectionSlideNo" />
    </span>
    <span class="spl-header-mark">Studio</span>
  </header>
</template>

<style scoped>
.spl-header {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  padding: 22px 78px 0;
  font-size: 12px;
  color: var(--slidev-theme-primary);
  font-weight: 720;
  letter-spacing: 0.12em;
  text-transform: uppercase;

  .spl-header-left {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .spl-header-mark {
    color: var(--studio-muted);
    letter-spacing: 0.18em;
  }
}
</style>
