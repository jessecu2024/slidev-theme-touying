<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const props = withDefaults(defineProps<{ ratio?: '50/50' | '40/60' | '60/40' | '35/65' | '65/35' }>(), {
  ratio: '50/50',
})
const { $frontmatter } = useSlideContext()

const columns = computed(() => {
  const [left, right] = props.ratio.split('/').map(Number)
  return `${left}fr ${right}fr`
})
</script>

<template>
  <div class="slidev-layout syd-split">
    <div v-if="$frontmatter.title || $slots.title" class="syd-split-title">
      <h1 v-if="$frontmatter.title">{{ $frontmatter.title }}</h1>
      <slot name="title" />
    </div>
    <div class="syd-split-grid" :style="{ gridTemplateColumns: columns }">
      <div class="syd-split-left"><slot /></div>
      <div class="syd-split-right"><slot name="right" /></div>
    </div>
  </div>
</template>

<style>
.tou-preset-sydney .slidev-layout.syd-split {
  display: grid;
  grid-template-rows: auto minmax(0, 1fr);
}

.tou-preset-sydney .syd-split-title:empty {
  display: none;
}

.tou-preset-sydney .syd-split-title h1 {
  margin-bottom: var(--space-5);
}

.tou-preset-sydney .syd-split-grid {
  display: grid;
  min-height: 0;
  gap: var(--space-7);
}

.tou-preset-sydney .syd-split-left,
.tou-preset-sydney .syd-split-right {
  min-width: 0;
}

.tou-preset-sydney .syd-split-right {
  padding-left: var(--space-6);
  border-left: 1px solid var(--border-subtle);
}
</style>
