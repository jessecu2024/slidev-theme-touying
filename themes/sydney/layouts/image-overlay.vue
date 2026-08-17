<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-image-overlay" :class="`syd-image-overlay-${$frontmatter.align || 'left'}`">
    <img
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :style="{ objectFit: $frontmatter.imageFit || 'cover', objectPosition: $frontmatter.imagePosition || 'center' }"
    >
    <div class="syd-image-overlay-shade" />
    <div class="syd-image-overlay-copy"><slot /></div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-image-overlay {
  position: relative;
  display: flex;
  padding: var(--space-8);
  align-items: center;
  background: var(--surface-dark);
}

.tou-preset-sydney .syd-image-overlay > img,
.tou-preset-sydney .syd-image-overlay-shade {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}

.tou-preset-sydney .syd-image-overlay-shade {
  background: linear-gradient(90deg, rgba(28, 28, 28, 0.78) 0%, rgba(28, 28, 28, 0.35) 48%, rgba(28, 28, 28, 0.08) 76%);
}

.tou-preset-sydney .syd-image-overlay-copy {
  position: relative;
  z-index: 1;
  width: min(100%, 560px);
}

.tou-preset-sydney .syd-image-overlay-copy h1,
.tou-preset-sydney .syd-image-overlay-copy h2,
.tou-preset-sydney .syd-image-overlay-copy p,
.tou-preset-sydney .syd-image-overlay-copy li {
  color: white !important;
}

.tou-preset-sydney .syd-image-overlay-copy .syd-eyebrow {
  color: rgba(255, 255, 255, 0.76) !important;
}

.tou-preset-sydney .syd-image-overlay-center {
  justify-content: center;
  text-align: center;
}

.tou-preset-sydney .syd-image-overlay-center .syd-image-overlay-shade {
  background: rgba(28, 28, 28, 0.45);
}

.tou-preset-sydney .syd-image-overlay-center .syd-image-overlay-copy {
  width: min(100%, 720px);
}

.tou-preset-sydney .syd-image-overlay-bottom-left {
  align-items: end;
}

.tou-preset-sydney .syd-image-overlay-bottom-left .syd-image-overlay-shade {
  background: linear-gradient(0deg, rgba(28, 28, 28, 0.8) 0%, rgba(28, 28, 28, 0.2) 58%, transparent 82%);
}
</style>
