<script setup lang="ts">
/**
 * Sandstone institutional cover slide.
 *
 * logo: if value.length <= 3 → emoji/text, rendered inline
 *       if value.length > 3  → treated as image URL, rendered as <img>
 *
 * author: single string, split by " and ", " & ", or ", "
 *         (if "and" present, never split by comma)
 */
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $slidev, $frontmatter } = useSlideContext()
const logo = computed(() => $frontmatter.logo ?? $slidev.nav.slides[0].meta.slide.frontmatter.logo)

function parseAuthors(raw: string | undefined): string[][] {
  if (!raw) return []
  let parts: string[]
  if (/\band\b/i.test(raw))
    parts = raw.split(/\s+and\s+/i).map(s => s.trim())
  else if (/&/.test(raw))
    parts = raw.split('&').map(s => s.trim())
  else
    parts = raw.split(',').map(s => s.trim())

  // chunk into rows of 3
  const chunks: string[][] = []
  for (let i = 0; i < parts.length; i += 3)
    chunks.push(parts.slice(i, i + 3))
  return chunks
}

const authorChunks = computed(() =>
  parseAuthors(($frontmatter as any)?.author ?? ($slidev as any)?.configs?.author),
)
</script>

<template>
  <div class="slidev-layout cover">
    <!-- Logo top-right -->
    <template v-if="logo">
      <img :src="logo" class="uni-cover-logo" />
    </template>

    <div class="uni-cover-inner">
      <div class="uni-cover-kicker">Sandstone / institutional</div>
      <!-- Title -->
      <div class="uni-cover-title">
        <slot name="title">{{ $slidev.configs.title }}</slot>
      </div>

      <!-- Subtitle -->
      <div v-if="$frontmatter.subtitle" class="uni-cover-subtitle">
        <slot name="subtitle">{{ $frontmatter.subtitle }}</slot>
      </div>

      <!-- Authors -->
      <div v-if="authorChunks.length" class="uni-cover-authors">
        <div
          v-for="(chunk, ci) in authorChunks"
          :key="ci"
          class="uni-cover-author-row"
          :style="{ gridTemplateColumns: `repeat(${chunk.length}, 1fr)` }"
        >
          <span v-for="(a, ai) in chunk" :key="ai">{{ a }}</span>
        </div>
      </div>

      <!-- Institution -->
      <div v-if="$frontmatter.institution" class="uni-cover-institution">
        {{ $frontmatter.institution }}
      </div>

      <!-- Date -->
      <div v-if="$frontmatter.date" class="uni-cover-date">
        {{ $frontmatter.date }}
      </div>

      <!-- Extra default slot content -->
      <div v-if="$slots.default" class="uni-cover-extra">
        <slot />
      </div>
    </div>
  </div>
</template>

<style>
.tou-preset-sandstone .slidev-layout.cover {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  background: #ffffff;
  width: 100%;
  height: 100%;
  padding: 76px 88px;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 24px;
    height: 100%;
    background: var(--slidev-theme-primary);
  }

  &::after {
    content: '';
    position: absolute;
    left: 24px;
    bottom: 0;
    width: 38%;
    height: 15px;
    background: var(--slidev-theme-secondary);
  }

  .uni-cover-logo {
    position: absolute;
    top: 56px;
    right: 68px;
    line-height: 1;
    height: 42px;
    width: auto;
    object-fit: contain;
  }

  .uni-cover-inner {
    text-align: left;
    width: 78%;
    padding: 0;
    box-sizing: border-box;
  }

  .uni-cover-kicker {
    color: var(--slidev-theme-primary);
    font-size: 0.66em;
    font-weight: 750;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    margin-bottom: 2.1em;
  }

  .uni-cover-title {
    font-size: 3em;
    font-weight: 720;
    color: var(--sandstone-ink);
    letter-spacing: -0.055em;
    line-height: 1;
    margin-bottom: 0.34em;
  }

  .uni-cover-subtitle {
    font-size: 1.05em;
    color: var(--sandstone-muted);
    line-height: 1.35;
    margin-bottom: 2.3em;
    max-width: 34em;
  }

  .uni-cover-authors {
    font-size: 0.73em;
    margin-top: 0.5em;
    color: var(--sandstone-ink);
  }

  .uni-cover-author-row {
    display: grid;
    column-gap: 2em;
    justify-items: start;
    margin-bottom: 0.45em;
  }

  .uni-cover-institution {
    font-size: 0.73em;
    margin-top: 1.3em;
    color: var(--slidev-theme-secondary);
    font-weight: 720;
  }

  .uni-cover-date {
    font-size: 0.68em;
    margin-top: 0.45em;
    color: var(--sandstone-muted);
  }

  .uni-cover-extra {
    margin-top: 0.8em;
    font-size: 0.8em;

    h1 {
      display: none;
    }
  }
}
</style>
