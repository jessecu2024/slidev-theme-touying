<script setup lang="ts">
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useSlideStructure } from '../../../composables/useSlideStructure'

const { slides } = useNav()
const { sections } = useSlideStructure()
const page = useNavigationCurrent()

const chapters = computed(() => sections.value.map((section, index) => {
  const sectionSlide = slides.value?.find(slide => slide.no === section.no)

  return {
    no: section.no,
    label: sectionSlide?.meta.slide.title || `Chapter ${index + 1}`,
    active: section.no === page.value,
  }
}))
</script>

<template>
  <div class="slidev-layout section">
    <div class="spl-overview">
      <h1 class="spl-overview-title">Contents</h1>

      <ol class="spl-overview-list">
        <li
          v-for="(chapter, index) in chapters"
          :key="chapter.no"
          class="spl-overview-item"
          :class="{ 'is-active': chapter.active }"
          :aria-current="chapter.active ? 'step' : undefined"
        >
          <span class="spl-overview-number">{{ String(index + 1).padStart(2, '0') }}</span>
          <span class="spl-overview-label">{{ chapter.label }}</span>
          <span v-if="chapter.active" class="spl-overview-current">Current chapter</span>
        </li>
      </ol>
    </div>
  </div>
</template>

<style>
:is(.tou-preset-simple, .tou-preset-simple-serif) .slidev-layout.section {
  width: 100%;
  height: 100%;
  display: block;
  box-sizing: border-box;
  padding: 36px 84px !important;
  background: #ffffff !important;

  .spl-overview {
    width: 100%;
    max-width: 820px;
    margin: 0 auto;
  }

  .spl-overview-title {
    margin: 0 0 0.8em !important;
    color: var(--slidev-theme-primary) !important;
    font-size: 1.8em !important;
    line-height: 1 !important;
  }

  .spl-overview-list {
    display: grid;
    gap: 10px;
    margin: 0;
    padding: 0;
    list-style: none;
  }

  .spl-overview-item {
    display: grid;
    grid-template-columns: 56px minmax(0, 1fr) auto;
    align-items: center;
    min-height: 54px;
    box-sizing: border-box;
    padding: 0 22px 0 0;
    overflow: hidden;
    background: #edf1f4;
    border-left: 6px solid var(--slidev-theme-primary);
    color: var(--slidev-theme-primary);
  }

  .spl-overview-item.is-active {
    background: var(--slidev-theme-primary);
    border-left-color: var(--slidev-theme-primary);
    color: #ffffff;
  }

  .spl-overview-number {
    text-align: center;
    font-family: var(--slidev-theme-font-sans, ui-sans-serif, system-ui, sans-serif);
    font-size: 0.55em;
    font-weight: 700;
    font-variant-numeric: tabular-nums;
    opacity: 0.72;
  }

  .spl-overview-label {
    font-size: 0.78em;
    font-weight: 600;
  }

  .spl-overview-current {
    font-family: var(--slidev-theme-font-sans, ui-sans-serif, system-ui, sans-serif);
    font-size: 0.45em;
    font-weight: 700;
    letter-spacing: 0;
    opacity: 0.82;
  }
}
</style>
