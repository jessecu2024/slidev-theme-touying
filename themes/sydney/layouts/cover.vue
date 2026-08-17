<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import ImageFrame from '../components/ImageFrame.vue'

const { $frontmatter } = useSlideContext()
const hasImage = computed(() => Boolean($frontmatter.image))
const align = computed(() => $frontmatter.align ?? (hasImage.value ? 'left' : 'center'))
</script>

<template>
  <div class="slidev-layout cover syd-cover" :class="[`syd-cover-${align}`, { 'syd-cover-has-image': hasImage }]">
    <div class="syd-cover-accent" />
    <div class="syd-cover-body">
      <div class="syd-cover-copy">
        <slot />
        <p v-if="$frontmatter.subtitle" class="syd-cover-subtitle">{{ $frontmatter.subtitle }}</p>
        <div v-if="$frontmatter.author || $frontmatter.date" class="syd-cover-meta">
          <span v-if="$frontmatter.author">{{ $frontmatter.author }}</span>
          <span v-if="$frontmatter.date">{{ $frontmatter.date }}</span>
        </div>
      </div>
      <ImageFrame
        v-if="hasImage"
        class="syd-cover-image"
        :src="$frontmatter.image"
        :alt="$frontmatter.imageAlt || ''"
        :fit="$frontmatter.imageFit || 'cover'"
        :position="$frontmatter.imagePosition || 'center'"
        radius="lg"
      />
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-cover {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-8);
  background: var(--surface-default);
}

.tou-preset-sydney .syd-cover-accent {
  position: absolute;
  top: 0;
  left: var(--space-8);
  width: 64px;
  height: 5px;
  background: var(--color-primary);
}

.tou-preset-sydney .syd-cover-body {
  display: grid;
  width: 100%;
  grid-template-columns: 1fr;
  align-items: center;
}

.tou-preset-sydney .syd-cover-copy {
  width: min(100%, 820px);
}

.tou-preset-sydney .syd-cover-center .syd-cover-copy {
  margin: 0 auto;
  text-align: center;
}

.tou-preset-sydney .syd-cover-left .syd-cover-copy {
  text-align: left;
}

.tou-preset-sydney .syd-cover h1 {
  max-width: none;
  margin: 0 !important;
  color: var(--text-primary) !important;
  font-size: 60px !important;
  font-weight: 750 !important;
  letter-spacing: -0.055em !important;
  line-height: 1.02 !important;
}

.tou-preset-sydney .syd-cover h1 + p:not(.syd-cover-subtitle) {
  margin-top: var(--space-5);
}

.tou-preset-sydney .syd-cover-subtitle,
.tou-preset-sydney .syd-cover-copy > p {
  max-width: 700px;
  margin: var(--space-5) 0 0;
  color: var(--text-secondary);
  font-size: 24px;
  line-height: 1.35;
}

.tou-preset-sydney .syd-cover-center .syd-cover-subtitle,
.tou-preset-sydney .syd-cover-center .syd-cover-copy > p {
  margin-right: auto;
  margin-left: auto;
}

.tou-preset-sydney .syd-cover-meta {
  display: flex;
  justify-content: inherit;
  gap: var(--space-5);
  margin-top: var(--space-7);
  color: var(--text-muted);
  font-size: 16px;
}

.tou-preset-sydney .syd-cover-center .syd-cover-meta {
  justify-content: center;
}

.tou-preset-sydney .syd-cover-has-image .syd-cover-body {
  grid-template-columns: minmax(0, 5fr) minmax(0, 4fr);
  gap: var(--space-7);
}

.tou-preset-sydney .syd-cover-has-image .syd-cover-image {
  height: 350px;
}

.tou-preset-sydney .syd-cover-has-image h1 {
  font-size: 52px !important;
}
</style>
