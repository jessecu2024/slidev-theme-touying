<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(defineProps<{
  type?: 'insight' | 'info' | 'warning' | 'risk' | 'neutral'
  label?: string
}>(), {
  type: 'insight',
})

const defaultLabels = {
  insight: 'Insight',
  info: 'Context',
  warning: 'Watch',
  risk: 'Risk',
  neutral: 'Note',
}

const displayLabel = computed(() => props.label ?? defaultLabels[props.type])
</script>

<template>
  <aside class="syd-callout" :class="`syd-callout-${type}`">
    <div class="syd-callout-label">{{ displayLabel }}</div>
    <div class="syd-callout-content"><slot /></div>
  </aside>
</template>

<style scoped>
.syd-callout {
  --callout-color: var(--color-primary);
  --callout-bg: var(--ochre-soft);
  margin: var(--space-5) 0;
  padding: var(--space-3) var(--space-5) var(--space-4);
  border-left: 3px solid var(--callout-color);
  background: color-mix(in srgb, var(--callout-bg) 72%, var(--surface-default));
}

.syd-callout-info {
  --callout-color: var(--color-blue);
  --callout-bg: var(--blue-soft);
}

.syd-callout-warning,
.syd-callout-risk {
  --callout-color: var(--color-red);
  --callout-bg: var(--red-soft);
}

.syd-callout-neutral {
  --callout-color: var(--color-charcoal);
  --callout-bg: var(--charcoal-soft);
}

.syd-callout-label {
  margin-bottom: var(--space-1);
  color: var(--callout-color);
  font-size: 13px;
  font-weight: 750;
  letter-spacing: 0.09em;
  line-height: 1.2;
  text-transform: uppercase;
}

.syd-callout-content {
  color: var(--text-primary);
  font-size: 18px;
  line-height: 1.4;
}

.syd-callout-content :deep(p:last-child) {
  margin-bottom: 0;
}
</style>
