<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import ImageFrame from '../components/ImageFrame.vue'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-image-split syd-image-left">
    <ImageFrame
      class="syd-image-split-visual"
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :fit="$frontmatter.imageFit || 'cover'"
      :position="$frontmatter.imagePosition || 'center'"
      :caption="$frontmatter.imageCaption"
      :radius="$frontmatter.imageRadius || 'md'"
    />
    <div class="syd-image-split-copy syd-image-left-copy"><slot /></div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-image-left {
  grid-template-columns: minmax(0, 54fr) minmax(0, 46fr);
}

.tou-preset-sydney .syd-image-left-copy {
  padding-left: var(--space-2);
}
</style>
