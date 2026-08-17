<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-image-full">
    <img
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :style="{ objectFit: $frontmatter.imageFit || 'cover', objectPosition: $frontmatter.imagePosition || 'center' }"
    >
    <div v-if="$slots.default" class="syd-image-full-copy" :class="{ 'syd-image-full-copy-overlay': $frontmatter.overlay }">
      <slot />
    </div>
    <div v-if="$frontmatter.imageCaption" class="syd-image-full-caption">{{ $frontmatter.imageCaption }}</div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-image-full {
  position: relative;
  padding: 0;
  background: var(--surface-dark);
}

.tou-preset-sydney .syd-image-full > img {
  width: 100%;
  height: 100%;
}

.tou-preset-sydney .syd-image-full-copy {
  position: absolute;
  top: var(--space-8);
  left: var(--space-8);
  max-width: 560px;
  color: white;
  text-shadow: 0 1px 10px rgba(0, 0, 0, 0.35);
}

.tou-preset-sydney .syd-image-full-copy-overlay {
  padding: var(--space-5);
  background: linear-gradient(90deg, rgba(28, 28, 28, 0.72), rgba(28, 28, 28, 0.15));
  text-shadow: none;
}

.tou-preset-sydney .syd-image-full-copy h1,
.tou-preset-sydney .syd-image-full-copy p {
  color: white !important;
}

.tou-preset-sydney .syd-image-full-caption {
  position: absolute;
  right: var(--space-5);
  bottom: var(--space-4);
  padding: 4px 7px;
  background: rgba(28, 28, 28, 0.55);
  color: rgba(255, 255, 255, 0.9);
  font-size: 12px;
  line-height: 1.2;
}
</style>
