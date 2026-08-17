<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'

type ImageItem = string | {
  src: string
  alt?: string
  caption?: string
  position?: string
}

const props = defineProps<{ images?: ImageItem[] }>()
const { $frontmatter } = useSlideContext()
const images = computed<ImageItem[]>(() => props.images ?? $frontmatter.images ?? [])
const normalized = computed(() => images.value.slice(0, 4).map(item =>
  typeof item === 'string' ? { src: item, alt: '', caption: '', position: 'center' } : item,
))
</script>

<template>
  <div class="slidev-layout syd-image-grid-layout">
    <div class="syd-image-grid-heading"><slot /></div>
    <div class="syd-image-grid" :class="`syd-image-grid-${normalized.length}`">
      <figure v-for="(item, index) in normalized" :key="index" class="syd-image-grid-item">
        <img :src="item.src" :alt="item.alt || ''" :style="{ objectPosition: item.position || 'center' }">
        <figcaption v-if="item.caption">{{ item.caption }}</figcaption>
      </figure>
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-image-grid-layout {
  display: grid;
  grid-template-rows: auto minmax(0, 1fr);
  gap: var(--space-4);
}

.tou-preset-sydney .syd-image-grid-heading h1 {
  margin-bottom: var(--space-3);
  font-size: 38px;
}

.tou-preset-sydney .syd-image-grid {
  display: grid;
  min-height: 0;
  gap: var(--space-3);
}

.tou-preset-sydney .syd-image-grid-2 {
  grid-template-columns: 3fr 2fr;
}

.tou-preset-sydney .syd-image-grid-3 {
  grid-template-columns: 3fr 2fr;
  grid-template-rows: 1fr 1fr;
}

.tou-preset-sydney .syd-image-grid-3 .syd-image-grid-item:first-child {
  grid-row: 1 / 3;
}

.tou-preset-sydney .syd-image-grid-4 {
  grid-template-columns: 1.25fr 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.tou-preset-sydney .syd-image-grid-4 .syd-image-grid-item:first-child {
  grid-row: 1 / 3;
}

.tou-preset-sydney .syd-image-grid-4 .syd-image-grid-item:nth-child(4) {
  grid-column: 2 / 4;
}

.tou-preset-sydney .syd-image-grid-item {
  position: relative;
  min-width: 0;
  min-height: 0;
  margin: 0;
}

.tou-preset-sydney .syd-image-grid-item img {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: var(--radius-sm);
  object-fit: cover;
}

.tou-preset-sydney .syd-image-grid-item figcaption {
  position: absolute;
  right: var(--space-2);
  bottom: var(--space-2);
  left: var(--space-2);
  padding: 4px 6px;
  background: rgba(28, 28, 28, 0.55);
  color: white;
  font-size: 12px;
  line-height: 1.2;
}
</style>
