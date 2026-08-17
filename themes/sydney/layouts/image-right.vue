<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import ImageFrame from '../components/ImageFrame.vue'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-image-split syd-image-right">
    <div class="syd-image-split-copy"><slot /></div>
    <ImageFrame
      class="syd-image-split-visual"
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :fit="$frontmatter.imageFit || 'cover'"
      :position="$frontmatter.imagePosition || 'center'"
      :caption="$frontmatter.imageCaption"
      :radius="$frontmatter.imageRadius || 'md'"
    />
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-image-split {
  display: grid;
  padding: var(--slide-margin-top) var(--slide-margin-x) var(--slide-margin-bottom);
  grid-template-columns: minmax(0, 46fr) minmax(0, 54fr);
  gap: var(--space-7);
  align-items: stretch;
}

.tou-preset-sydney .syd-image-split-copy {
  min-width: 0;
  align-self: center;
  font-size: 19px;
  line-height: 1.4;
}

.tou-preset-sydney .syd-image-split-copy h1 {
  font-size: 40px;
}

.tou-preset-sydney .syd-image-split-copy li {
  margin: 0.22em 0;
}

.tou-preset-sydney .syd-image-split-visual {
  height: calc(540px - var(--slide-margin-top) - var(--slide-margin-bottom));
}
</style>
