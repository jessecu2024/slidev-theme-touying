<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
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
  <div class="slidev-layout cover new-cover">
    <div class="new-cover-body">
      <div class="new-cover-kicker">NEW · SIMPLE WITH PROGRESS</div>
      <slot />
      <div v-if="authors.length" class="new-cover-authors">
        <span v-for="(author, index) in authors" :key="index">{{ author }}</span>
      </div>
      <div v-if="$frontmatter.date" class="new-cover-date">{{ $frontmatter.date }}</div>
    </div>
  </div>
</template>

<style>
.tou-preset-new .slidev-layout.new-cover {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 72px;
  box-sizing: border-box;
  background: #ffffff !important;

  .new-cover-body {
    width: min(780px, 86%);
    text-align: center;
  }

  .new-cover-kicker {
    margin-bottom: 28px;
    color: var(--slidev-theme-primary);
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.15em;
  }

  h1 {
    margin: 0 0 24px !important;
    color: var(--new-ink) !important;
    font-size: 2.65em !important;
    font-weight: 720 !important;
    line-height: 1.02;
    letter-spacing: -0.055em;
  }

  p {
    max-width: 30em;
    margin: 0.4em auto;
    color: var(--new-muted);
    font-size: 1.02em;
    line-height: 1.4;
  }

  .new-cover-authors {
    display: flex;
    justify-content: center;
    gap: 28px;
    margin-top: 48px;
    color: var(--new-ink);
    font-size: 0.72em;
    font-weight: 600;
  }

  .new-cover-date {
    margin-top: 8px;
    color: var(--new-muted);
    font-size: 0.68em;
  }
}
</style>
