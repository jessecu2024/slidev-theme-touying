<script setup lang="ts">
import TitleRenderer from '#slidev/title-renderer'
import { useSlideContext } from '@slidev/client'

const { $frontmatter, $page } = useSlideContext()
</script>

<template>
  <div class="slidev-layout section syd-section" :class="`syd-section-${$frontmatter.variant || 'light'}`">
    <div class="syd-section-index">{{ $frontmatter.sectionNumber || String($page).padStart(2, '0') }}</div>
    <div class="syd-section-rule" />
    <div class="syd-section-body">
      <div v-if="$frontmatter.eyebrow" class="syd-section-eyebrow">{{ $frontmatter.eyebrow }}</div>
      <div class="syd-section-title"><TitleRenderer class="tou-title" :no="$page" /></div>
      <div class="syd-section-extra"><slot /></div>
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-section {
  position: relative;
  display: grid;
  padding: var(--space-8);
  grid-template-columns: 80px 1fr;
  grid-template-rows: 1fr;
  gap: var(--space-6);
  align-items: center;
  background: var(--surface-default);
}

.tou-preset-sydney .syd-section-index {
  align-self: start;
  color: var(--color-primary);
  font-size: 16px;
  font-weight: 750;
  font-variant-numeric: tabular-nums;
  letter-spacing: 0.08em;
}

.tou-preset-sydney .syd-section-rule {
  position: absolute;
  top: var(--space-8);
  bottom: var(--space-8);
  left: 144px;
  width: 1px;
  background: var(--border-subtle);
}

.tou-preset-sydney .syd-section-body {
  max-width: 720px;
  margin-left: var(--space-6);
}

.tou-preset-sydney .syd-section-title {
  color: var(--text-primary);
  font-size: 52px;
  font-weight: 750;
  letter-spacing: -0.045em;
  line-height: 1.05;
}

.tou-preset-sydney .syd-section-eyebrow {
  margin-bottom: var(--space-4);
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 750;
  letter-spacing: 0.105em;
  text-transform: uppercase;
}

.tou-preset-sydney .syd-section-extra h1 {
  display: none;
}

.tou-preset-sydney .syd-section-extra p {
  max-width: 600px;
  margin: var(--space-5) 0 0;
  color: var(--text-secondary);
  font-size: 20px;
}

.tou-preset-sydney .syd-section-dark {
  background: var(--surface-dark) !important;
}

.tou-preset-sydney .syd-section-dark .syd-section-title,
.tou-preset-sydney .syd-section-dark .syd-section-extra p {
  color: var(--text-inverse);
}

.tou-preset-sydney .syd-section-dark .syd-section-rule {
  background: rgba(255, 255, 255, 0.2);
}
</style>
