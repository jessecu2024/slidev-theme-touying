<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-big-number" :class="`syd-big-number-${$frontmatter.accent || 'ochre'}`">
    <div class="syd-big-number-value">{{ $frontmatter.value }}</div>
    <div v-if="$frontmatter.label" class="syd-big-number-label">{{ $frontmatter.label }}</div>
    <div class="syd-big-number-extra"><slot /></div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-big-number {
  --big-number-color: var(--color-primary);
  display: flex;
  padding: var(--space-9);
  flex-direction: column;
  justify-content: center;
  background: var(--surface-default);
  text-align: center;
}

.tou-preset-sydney .slidev-layout.syd-big-number.syd-big-number-blue { --big-number-color: var(--color-blue); }
.tou-preset-sydney .slidev-layout.syd-big-number.syd-big-number-red { --big-number-color: var(--color-red); }
.tou-preset-sydney .slidev-layout.syd-big-number.syd-big-number-charcoal { --big-number-color: var(--color-charcoal); }

.tou-preset-sydney .syd-big-number-value {
  color: var(--big-number-color);
  font-size: 132px;
  font-weight: 760;
  font-variant-numeric: tabular-nums;
  letter-spacing: -0.075em;
  line-height: 0.88;
}

.tou-preset-sydney .syd-big-number-label {
  max-width: 760px;
  margin: var(--space-5) auto 0;
  color: var(--text-primary);
  font-size: 32px;
  font-weight: 650;
  letter-spacing: -0.025em;
  line-height: 1.15;
}

.tou-preset-sydney .syd-big-number-extra {
  max-width: 620px;
  margin: var(--space-4) auto 0;
  color: var(--text-secondary);
  font-size: 18px;
}

.tou-preset-sydney .syd-big-number-extra h1 {
  display: none;
}
</style>
