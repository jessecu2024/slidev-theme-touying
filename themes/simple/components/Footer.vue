<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import { useNavigationCurrent } from '../../../composables/useNavigationTransition'

const { $nav } = useSlideContext()
const page = useNavigationCurrent()
const total = computed(() => $nav.value?.slides.length ?? 1)
</script>

<template>
  <footer class="spl-footer">
    <span class="spl-footer-right">{{ page }} / {{ total }}</span>
  </footer>
</template>

<style scoped>
.spl-footer {
  position: absolute;
  bottom: 28px;
  left: 0;
  right: 0;
  display: flex;
  justify-content: flex-end;
  align-items: baseline;
  padding: 0 64px;
  font-size: 0.6em;
  color: var(--spl-deco);
}
</style>
