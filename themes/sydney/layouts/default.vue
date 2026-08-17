<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout default syd-default" :class="$frontmatter.background ? `bg-${$frontmatter.background}` : ''">
    <div v-if="$frontmatter.eyebrow" class="syd-default-eyebrow">{{ $frontmatter.eyebrow }}</div>
    <div class="syd-default-content"><slot /></div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-default {
  position: relative;
}

.tou-preset-sydney .syd-default-eyebrow {
  margin-bottom: var(--space-3);
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 750;
  letter-spacing: 0.105em;
  line-height: 1.15;
  text-transform: uppercase;
}

.tou-preset-sydney .syd-default-content {
  width: min(100%, 860px);
}

.tou-preset-sydney .syd-default-content > :first-child {
  margin-top: 0;
}
</style>
