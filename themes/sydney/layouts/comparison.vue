<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-comparison">
    <div v-if="$frontmatter.title || $slots.title" class="syd-comparison-title">
      <h1 v-if="$frontmatter.title">{{ $frontmatter.title }}</h1>
      <slot name="title" />
    </div>
    <div class="syd-comparison-grid">
      <section class="syd-comparison-side">
        <div class="syd-comparison-label syd-comparison-label-left">{{ $frontmatter.leftLabel || 'Option A' }}</div>
        <slot />
      </section>
      <section class="syd-comparison-side syd-comparison-side-right">
        <div class="syd-comparison-label syd-comparison-label-right">{{ $frontmatter.rightLabel || 'Option B' }}</div>
        <slot name="right" />
      </section>
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-comparison {
  display: grid;
  grid-template-rows: auto minmax(0, 1fr);
}

.tou-preset-sydney .syd-comparison-title:empty {
  display: none;
}

.tou-preset-sydney .syd-comparison-title h1 {
  margin-bottom: var(--space-4);
}

.tou-preset-sydney .syd-comparison-grid {
  display: grid;
  min-height: 0;
  grid-template-columns: 1fr 1fr;
}

.tou-preset-sydney .syd-comparison-side {
  min-width: 0;
  padding: var(--space-4) var(--space-7) 0 0;
}

.tou-preset-sydney .syd-comparison-side-right {
  padding-right: 0;
  padding-left: var(--space-7);
  border-left: 1px solid var(--border-subtle);
}

.tou-preset-sydney .syd-comparison-label {
  margin-bottom: var(--space-5);
  color: var(--color-primary);
  font-size: 14px;
  font-weight: 750;
  letter-spacing: 0.09em;
  text-transform: uppercase;
}

.tou-preset-sydney .syd-comparison-label-right {
  color: var(--color-blue);
}
</style>
