<script setup lang="ts">
/**
 * Harbour top navigation rail.
 *
 * Each section is a column. Inside each column:
 *   - Section title (click → section slide)
 *   - Dots grouped by subsection (one row per subsection) if linebreaks is
 *     effectively true, otherwise all dots in a single row.
 *
 * miniSlides.linebreaks:
 *   true  — always one row per subsection
 *   false — always one row for all slides
 *   auto  — one row per subsection only if max subsections across all sections <= 3
 */
import TitleRenderer from '#slidev/title-renderer'
import { useNav } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'
import { useCurrentSectionIndex, useSlideStructure } from '../../../composables/useSlideStructure'
import { useTouyingConfig } from '../../../composables/useTouyingConfig'

const { go } = useNav()
const page = useNavigationCurrent()
const { sections } = useSlideStructure()
const currentSectionIndex = useCurrentSectionIndex()
const config = useTouyingConfig()

const useLinebreaks = computed(() => {
  if (!config.value.miniSlides.subsection) return false
  const setting = config.value.miniSlides.linebreaks ?? 'auto'
  if (setting === 'auto') return sections.value.every(s => s.subsections.length <= 3)
  if (setting === true) return true
  if (setting === false) return false
  console.error(`Invalid miniSlides.linebreaks value: ${setting}`)
})

const showDots = computed(() => config.value.miniSlides.subsection)
</script>

<template>
  <nav class="dew-mini-slides" aria-label="Section navigation">
    <div
      v-for="(section, idx) in sections"
      :key="section.no"
      class="dew-mini-slides-section"
      :class="{ inactive: idx !== currentSectionIndex }"
    >
      <!-- Section name -->
      <span class="dew-mini-slides-section-title" @click="go(section.no)">
        <TitleRenderer class="tou-title" :no="section.no" />
      </span>

      <!-- One row of dots per subsection (linebreaks) or single row -->
      <template v-if="showDots">
        <template v-if="useLinebreaks && section.subsections.length">
          <div
            v-for="sub in section.subsections"
            :key="sub.no"
            class="dew-mini-slides-dots"
          >
            <span
              v-if="sub.no !== section.no"
              class="dew-mini-dot"
              :class="{ filled: sub.no === page }"
              :title="`Slide ${sub.no}`"
              @click="go(sub.no)"
            />
            <span
              v-for="slideNo in sub.slides"
              :key="slideNo"
              class="dew-mini-dot"
              :class="{ filled: slideNo === page }"
              :title="`Slide ${slideNo}`"
              @click="go(slideNo)"
            />
          </div>
        </template>
        <!-- Single row -->
        <div v-else class="dew-mini-slides-dots">
          <span
            v-for="slideNo in section.slides"
            :key="slideNo"
            class="dew-mini-dot"
            :class="{ filled: slideNo === page }"
            :title="`Slide ${slideNo}`"
            @click="go(slideNo)"
          />
        </div>
      </template>
    </div>
  </nav>
</template>

<style scoped>
.dew-mini-slides {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  padding: 18px 74px 14px;
  gap: 24px;
  font-size: 13px;
  box-sizing: border-box;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.97);
  border-bottom: 1px solid var(--harbour-line);
}

.dew-mini-slides-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex: 1 1 0;
  min-width: 0;
  transition: opacity 0.3s ease;
  white-space: nowrap;
}

.dew-mini-slides-section.inactive {
  opacity: 0.45;
}

.dew-mini-slides-section-title {
  font-weight: 700;
  color: var(--slidev-theme-primary);
  line-height: 1.2;
  cursor: pointer;
  letter-spacing: -0.01em;
  max-width: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
}

.dew-mini-slides-section.inactive .dew-mini-slides-section-title {
  color: var(--harbour-ink);
}

.dew-mini-slides-dots {
  display: flex;
  flex-direction: row;
  gap: 4px;
  margin-top: 7px;
  margin-left: 0;
  min-height: 4px;
}

.dew-mini-dot {
  display: inline-block;
  width: 14px;
  height: 3px;
  border-radius: 0;
  border: 0;
  background: var(--harbour-line);
  cursor: pointer;
  transition: background 0.2s ease, border-color 0.2s ease;
  flex-shrink: 0;
}

.dew-mini-dot.filled {
  background: var(--slidev-theme-primary);
}

.dew-mini-slides-section.inactive .dew-mini-dot {
  background: #c8d2df;
}

.dew-mini-slides-section.inactive .dew-mini-dot.filled {
  background: var(--harbour-ink);
}
</style>
