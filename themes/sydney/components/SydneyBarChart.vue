<script setup lang="ts">
import { computed } from 'vue'

type Accent = 'ochre' | 'blue' | 'red' | 'charcoal' | 'gray'

interface BarItem {
  label: string
  value: number
  display?: string
  accent?: Accent
}

const props = withDefaults(defineProps<{
  items: BarItem[]
  max?: number
  compact?: boolean
}>(), {
  compact: false,
})

const scaleMax = computed(() => props.max || Math.max(...props.items.map(item => item.value), 1))

function width(value: number) {
  return `${Math.max(1.5, Math.min(100, value / scaleMax.value * 100))}%`
}
</script>

<template>
  <div class="syd-bars" :class="{ 'syd-bars-compact': compact }" role="img" aria-label="Bar chart">
    <div v-for="item in items" :key="item.label" class="syd-bars-row">
      <span class="syd-bars-label">{{ item.label }}</span>
      <span class="syd-bars-track">
        <i :class="`syd-bars-${item.accent || 'charcoal'}`" :style="{ width: width(item.value) }" />
      </span>
      <strong>{{ item.display ?? item.value }}</strong>
    </div>
  </div>
</template>

<style scoped>
.syd-bars {
  display: grid;
  gap: 17px;
  width: 100%;
}

.syd-bars-row {
  display: grid;
  grid-template-columns: 124px minmax(0, 1fr) 64px;
  gap: 13px;
  align-items: center;
}

.syd-bars-label {
  color: var(--text-secondary);
  font-size: 15px;
  line-height: 1.15;
}

.syd-bars-track {
  display: block;
  height: 22px;
  background: var(--surface-subtle);
}

.syd-bars-track i {
  display: block;
  height: 100%;
  background: var(--chart-neutral-2);
}

.syd-bars-track .syd-bars-ochre { background: var(--chart-1); }
.syd-bars-track .syd-bars-blue { background: var(--chart-2); }
.syd-bars-track .syd-bars-red { background: var(--chart-negative); }
.syd-bars-track .syd-bars-charcoal { background: var(--chart-neutral-1); }
.syd-bars-track .syd-bars-gray { background: var(--chart-neutral-3); }

.syd-bars-row strong {
  color: var(--text-primary);
  font-size: 15px;
  font-variant-numeric: tabular-nums;
  text-align: right;
}

.syd-bars-compact { gap: 11px; }
.syd-bars-compact .syd-bars-row { grid-template-columns: 105px minmax(0, 1fr) 56px; }
.syd-bars-compact .syd-bars-track { height: 16px; }
</style>
