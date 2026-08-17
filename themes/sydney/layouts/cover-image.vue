<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import ImageFrame from '../components/ImageFrame.vue'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-cover-image-layout">
    <div class="syd-cover-image-copy">
      <div class="syd-cover-image-accent" />
      <slot />
      <p v-if="$frontmatter.subtitle" class="syd-cover-image-subtitle">{{ $frontmatter.subtitle }}</p>
      <div v-if="$frontmatter.author || $frontmatter.date" class="syd-cover-image-meta">
        <span v-if="$frontmatter.author">{{ $frontmatter.author }}</span>
        <span v-if="$frontmatter.date">{{ $frontmatter.date }}</span>
      </div>
    </div>
    <ImageFrame
      class="syd-cover-image-visual"
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :fit="$frontmatter.imageFit || 'cover'"
      :position="$frontmatter.imagePosition || 'center'"
      radius="none"
    />
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-cover-image-layout {
  display: grid;
  padding: 0;
  grid-template-columns: 45% 55%;
  background: var(--surface-default);
}

.tou-preset-sydney .syd-cover-image-copy {
  position: relative;
  display: flex;
  min-width: 0;
  padding: var(--space-7) var(--space-8);
  flex-direction: column;
  justify-content: center;
}

.tou-preset-sydney .syd-cover-image-accent {
  position: absolute;
  top: var(--space-7);
  width: 56px;
  height: 5px;
  background: var(--color-primary);
}

.tou-preset-sydney .syd-cover-image-copy h1 {
  max-width: none;
  margin: 0 !important;
  font-size: 52px !important;
  font-weight: 750 !important;
  letter-spacing: -0.052em !important;
  line-height: 1.03 !important;
}

.tou-preset-sydney .syd-cover-image-copy > p,
.tou-preset-sydney .syd-cover-image-subtitle {
  margin: var(--space-5) 0 0;
  color: var(--text-secondary);
  font-size: 21px;
  line-height: 1.35;
}

.tou-preset-sydney .syd-cover-image-meta {
  display: flex;
  gap: var(--space-4);
  margin-top: var(--space-7);
  color: var(--text-muted);
  font-size: 15px;
}

.tou-preset-sydney .syd-cover-image-visual {
  height: 100%;
}
</style>
