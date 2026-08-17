<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import ImageFrame from '../components/ImageFrame.vue'
import Quote from '../components/Quote.vue'

const { $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout syd-quote-image">
    <ImageFrame
      class="syd-quote-image-visual"
      :src="$frontmatter.image"
      :alt="$frontmatter.imageAlt || ''"
      :fit="$frontmatter.imageFit || 'cover'"
      :position="$frontmatter.imagePosition || 'center'"
      radius="md"
    />
    <div class="syd-quote-image-copy">
      <Quote :author="$frontmatter.author" :role="$frontmatter.role" :accent="$frontmatter.accent || 'ochre'">
        <slot />
      </Quote>
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-quote-image {
  display: grid;
  grid-template-columns: minmax(0, 40fr) minmax(0, 60fr);
  gap: var(--space-8);
  align-items: stretch;
}

.tou-preset-sydney .syd-quote-image-visual {
  height: calc(540px - var(--slide-margin-top) - var(--slide-margin-bottom));
}

.tou-preset-sydney .syd-quote-image-copy {
  align-self: center;
}

.tou-preset-sydney .syd-quote-image-copy h1 {
  display: none;
}
</style>
