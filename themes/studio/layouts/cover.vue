<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()

// Parse "Alpha and Bravo and Charlie" or "Alpha, Bravo, Charlie" into array
const authors = computed<string[]>(() => {
  const raw: string | string[] | undefined = $frontmatter.authors ?? $frontmatter.author
  if (!raw) return []
  if (Array.isArray(raw)) return raw
  if (/\band\b/i.test(raw)) return raw.split(/\s+and\s+/i).map(s => s.trim())
  if (/&/.test(raw)) return raw.split('&').map(s => s.trim())
  return raw.split(',').map(s => s.trim())
})
</script>

<template>
  <div class="slidev-layout cover">
    <div class="spl-cover-body">
      <div class="spl-cover-kicker">Studio / minimal expression</div>

      <slot />

      <!-- Structured authors from frontmatter (rendered as a row) -->
      <div v-if="authors.length" class="spl-cover-authors">
        <span v-for="(a, i) in authors" :key="i" class="spl-cover-author">{{ a }}</span>
      </div>

      <!-- Date from frontmatter -->
      <div v-if="$frontmatter.date" class="spl-cover-date">{{ $frontmatter.date }}</div>
    </div>
  </div>
</template>

<style>
.tou-preset-studio .slidev-layout.cover {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: flex-end;
  justify-content: flex-start;
  padding: 76px 82px 88px;
  box-sizing: border-box;
  background: #ffffff;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 21%;
    height: 100%;
    background: var(--studio-lilac);
  }

  &::after {
    content: '';
    position: absolute;
    top: 0;
    right: 21%;
    width: 11px;
    height: 42%;
    background: var(--slidev-theme-secondary);
  }

  .spl-cover-body {
    position: relative;
    text-align: left;
    width: 68%;
    z-index: 1;
  }

  .spl-cover-kicker {
    color: var(--slidev-theme-primary);
    font-size: 0.63em;
    font-weight: 760;
    letter-spacing: 0.17em;
    text-transform: uppercase;
    margin-bottom: 2em;
  }

  h1 {
    font-size: 3.3em !important;
    font-weight: 760 !important;
    color: var(--studio-ink) !important;
    letter-spacing: -0.065em;
    line-height: 0.94;
    margin: 0 0 0.42em !important;
  }

  p {
    color: var(--studio-muted);
    margin: 0.4em 0;
    max-width: 28em;
  }

  .spl-cover-authors {
    display: flex;
    justify-content: flex-start;
    gap: 1.5em;
    margin-top: 1.8em;
    color: var(--studio-ink);
    font-size: 0.72em;
    font-weight: 650;
  }

  .spl-cover-date {
    margin-top: 0.7em;
    color: var(--studio-muted);
    font-size: 0.68em;
  }
}
</style>
