<script setup lang="ts">
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useSlideStructure } from '../../../composables/useSlideStructure'

const { slides } = useNav()
const { sections } = useSlideStructure()
const page = useNavigationCurrent()

const activeChapter = computed(() => {
  let active = -1

  sections.value.forEach((section, index) => {
    if (section.no <= page.value)
      active = index
  })

  return active
})

const chapters = computed(() => sections.value.map((section, index) => {
  const sectionSlide = slides.value?.find(slide => slide.no === section.no)

  return {
    no: section.no,
    label: sectionSlide?.meta.slide.title || `Chapter ${index + 1}`,
    active: index === activeChapter.value,
  }
}))
</script>

<template>
  <nav
    v-if="chapters.length"
    class="spl-chapter-progress"
    aria-label="Chapter progress"
  >
    <ol class="spl-chapter-list">
      <li
        v-for="(chapter, index) in chapters"
        :key="chapter.no"
        class="spl-chapter"
        :class="{ 'is-active': chapter.active }"
        :aria-current="chapter.active ? 'step' : undefined"
      >
        <span class="spl-chapter-label">
          <span class="spl-chapter-number">{{ String(index + 1).padStart(2, '0') }}</span>
          <span class="spl-chapter-title">{{ chapter.label }}</span>
        </span>
      </li>
    </ol>
  </nav>
</template>

<style scoped>
.spl-chapter-progress {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 12;
  box-sizing: border-box;
  height: 20px;
  font-family: var(--slidev-theme-font-sans, ui-sans-serif, system-ui, sans-serif);
}

.spl-chapter-list {
  display: flex;
  align-items: stretch;
  gap: 0;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  list-style: none;
}

.spl-chapter {
  display: flex;
  flex: 1 1 0;
  align-items: center;
  justify-content: center;
  min-width: 0;
  background: var(--spl-chapter-track);
  color: #ffffff;
  transition: background-color 0.28s ease;
}

.spl-chapter:nth-child(even) {
  background: var(--spl-chapter-track-alt);
}

.spl-chapter-label {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5em;
  width: 100%;
  min-width: 0;
  padding: 0 8px;
  font-size: 8px;
  font-weight: 600;
  line-height: 1.15;
  letter-spacing: 0.015em;
}

.spl-chapter-number {
  flex: 0 0 auto;
  font-variant-numeric: tabular-nums;
  opacity: 0.72;
}

.spl-chapter-title {
  display: block;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.spl-chapter.is-active {
  background: var(--slidev-theme-primary);
  color: #ffffff;
}

.spl-chapter.is-active .spl-chapter-label {
  font-weight: 700;
}

</style>
