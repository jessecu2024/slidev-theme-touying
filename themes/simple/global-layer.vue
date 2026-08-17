<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent, useNavigationTransition } from '../../composables/useNavigationTransition'
import Footer from './components/Footer.vue'
import SectionProgress from './components/SectionProgress.vue'

const { $nav } = useSlideContext()
const page = useNavigationCurrent()

const frontmatter = computed(() => $nav.value.currentSlideRoute.meta.slide.frontmatter)
const total = computed(() => $nav.value.slides.length)

const hideFooter = computed(() => frontmatter.value.footer === false || ['cover', 'focus', 'section', 'end'].includes($nav.value.currentLayout))
const FooterTransition = useNavigationTransition(hideFooter)

const hideChapterProgress = computed(() =>
  frontmatter.value.chapterProgress === false
  || page.value === 1
  || page.value === total.value
  || ['section', 'outline', 'end'].includes($nav.value.currentLayout),
)
const ChapterProgressTransition = useNavigationTransition(hideChapterProgress)
</script>

<template>
  <div class="tou-layer">
    <FooterTransition>
      <Footer />
    </FooterTransition>
    <ChapterProgressTransition>
      <SectionProgress />
    </ChapterProgressTransition>
  </div>
</template>
