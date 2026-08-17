<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import ImageFrame from '../components/ImageFrame.vue'
import Metric from '../components/Metric.vue'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-metric-image">
    <div class="syd-metric-image-copy">
      <Metric
        :value="$frontmatter.value"
        :label="$frontmatter.label"
        :note="$frontmatter.note"
        :accent="$frontmatter.accent || 'ochre'"
      />
      <div class="syd-metric-image-extra"><slot /></div>
    </div>
    <ImageFrame
      class="syd-metric-image-visual"
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :fit="$frontmatter.imageFit || 'cover'"
      :position="$frontmatter.imagePosition || 'center'"
      :caption="$frontmatter.imageCaption"
      radius="md"
    />
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-metric-image {
  display: grid;
  grid-template-columns: minmax(0, 42fr) minmax(0, 58fr);
  gap: var(--space-7);
  align-items: stretch;
}

.tou-preset-sydney .syd-metric-image-copy {
  align-self: center;
}

.tou-preset-sydney .syd-metric-image-extra {
  margin-top: var(--space-6);
  color: var(--text-secondary);
  font-size: 19px;
}

.tou-preset-sydney .syd-metric-image-extra h1 {
  display: none;
}

.tou-preset-sydney .syd-metric-image-visual {
  height: calc(540px - var(--slide-margin-top) - var(--slide-margin-bottom));
}
</style>
