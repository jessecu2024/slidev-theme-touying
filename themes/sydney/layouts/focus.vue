<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div
    class="slidev-layout focus syd-focus"
    :class="[`syd-focus-${$frontmatter.accent || 'ochre'}`, `syd-focus-${$frontmatter.align || 'center'}`]"
  >
    <div class="syd-focus-rule" />
    <div class="syd-focus-content"><slot /></div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-focus {
  --focus-bg: var(--color-primary);
  --focus-fg: var(--text-inverse);
  --focus-rule: rgba(255, 255, 255, 0.75);
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-9);
  background: var(--focus-bg);
  color: var(--focus-fg);
}

.tou-preset-sydney .slidev-layout.syd-focus.syd-focus-charcoal {
  --focus-bg: var(--surface-dark);
}

.tou-preset-sydney .slidev-layout.syd-focus.syd-focus-blue {
  --focus-bg: var(--color-blue);
}

.tou-preset-sydney .slidev-layout.syd-focus.syd-focus-light {
  --focus-bg: var(--surface-default);
  --focus-fg: var(--text-primary);
  --focus-rule: var(--color-primary);
}

.tou-preset-sydney .syd-focus-rule {
  position: absolute;
  top: var(--space-8);
  width: 56px;
  height: 4px;
  background: var(--focus-rule);
}

.tou-preset-sydney .syd-focus-content {
  width: min(100%, 780px);
  text-align: center;
}

.tou-preset-sydney .syd-focus-left .syd-focus-content {
  margin-right: auto;
  text-align: left;
}

.tou-preset-sydney .syd-focus h1,
.tou-preset-sydney .syd-focus p {
  color: var(--focus-fg) !important;
}

.tou-preset-sydney .syd-focus h1 {
  max-width: none;
  margin: 0 !important;
  font-size: 54px !important;
  font-weight: 750 !important;
  letter-spacing: -0.05em !important;
  line-height: 1.06 !important;
}

.tou-preset-sydney .syd-focus p {
  margin-top: var(--space-5);
  font-size: 22px;
  opacity: 0.86;
}
</style>
