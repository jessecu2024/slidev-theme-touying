<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationTransition } from '../../composables/useNavigationTransition'
import Footer from './components/Footer.vue'

const { $nav } = useSlideContext()
const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
const chromeFreeLayouts = [
  'cover',
  'cover-image',
  'focus',
  'section',
  'image-full',
  'image-overlay',
  'end',
]
const hideFooter = computed(() =>
  frontmatter.value.footer === false || chromeFreeLayouts.includes($nav.value.currentLayout),
)
const FooterTransition = useNavigationTransition(hideFooter)
</script>

<template>
  <div class="tou-layer">
    <FooterTransition>
      <Footer />
    </FooterTransition>
  </div>
</template>
