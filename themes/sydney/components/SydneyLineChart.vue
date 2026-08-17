<script setup lang="ts">
import { computed } from 'vue'

type Accent = 'ochre' | 'blue' | 'red' | 'charcoal' | 'gray'

interface LineSeries {
  name: string
  values: number[]
  accent?: Accent
}

const props = withDefaults(defineProps<{
  labels: string[]
  series: LineSeries[]
  min?: number
  max?: number
  suffix?: string
}>(), {
  suffix: '',
})

const values = computed(() => props.series.flatMap(item => item.values))
const lower = computed(() => props.min ?? Math.min(...values.value, 0))
const upper = computed(() => props.max ?? Math.max(...values.value, 1))
const span = computed(() => Math.max(upper.value - lower.value, 1))

function x(index: number) {
  return 60 + index * (670 / Math.max(props.labels.length - 1, 1))
}

function y(value: number) {
  return 210 - (value - lower.value) / span.value * 165
}

function points(series: LineSeries) {
  return series.values.map((value, index) => `${x(index)},${y(value)}`).join(' ')
}

const ticks = computed(() => [upper.value, lower.value + span.value / 2, lower.value])
</script>

<template>
  <figure class="syd-line-chart" role="img" aria-label="Line chart">
    <svg viewBox="0 0 760 245" preserveAspectRatio="none">
      <g class="syd-line-grid">
        <line v-for="(tick, index) in ticks" :key="tick" x1="60" x2="730" :y1="45 + index * 82.5" :y2="45 + index * 82.5" />
      </g>
      <g class="syd-line-axis-labels">
        <text v-for="(tick, index) in ticks" :key="tick" x="50" :y="49 + index * 82.5" text-anchor="end">{{ tick }}{{ suffix }}</text>
        <text v-for="(label, index) in labels" :key="label" :x="x(index)" y="236" text-anchor="middle">{{ label }}</text>
      </g>
      <g v-for="item in series" :key="item.name" :class="`syd-line-${item.accent || 'charcoal'}`">
        <polyline :points="points(item)" />
        <circle v-for="(value, index) in item.values" :key="index" :cx="x(index)" :cy="y(value)" r="4" />
      </g>
    </svg>
    <figcaption>
      <span v-for="item in series" :key="item.name" :class="`syd-line-key-${item.accent || 'charcoal'}`">{{ item.name }}</span>
    </figcaption>
  </figure>
</template>

<style scoped>
.syd-line-chart {
  width: 100%;
  margin: 0;
}

.syd-line-chart svg {
  display: block;
  width: 100%;
  height: 245px;
  overflow: visible;
}

.syd-line-grid line {
  stroke: var(--border-subtle);
  stroke-width: 1;
}

.syd-line-axis-labels {
  fill: var(--text-muted);
  font-family: var(--syd-font-sans);
  font-size: 11px;
}

.syd-line-chart polyline {
  fill: none;
  stroke: var(--chart-neutral-1);
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-width: 4;
}

.syd-line-chart circle {
  fill: var(--surface-default);
  stroke: var(--chart-neutral-1);
  stroke-width: 3;
}

.syd-line-ochre polyline, .syd-line-ochre circle { stroke: var(--chart-1); }
.syd-line-blue polyline, .syd-line-blue circle { stroke: var(--chart-2); }
.syd-line-red polyline, .syd-line-red circle { stroke: var(--chart-negative); }
.syd-line-charcoal polyline, .syd-line-charcoal circle { stroke: var(--chart-neutral-1); }
.syd-line-gray polyline, .syd-line-gray circle { stroke: var(--chart-neutral-3); }

.syd-line-chart figcaption {
  display: flex;
  justify-content: flex-end;
  gap: 22px;
  margin-top: 5px;
  color: var(--text-secondary);
  font-size: 13px;
}

.syd-line-chart figcaption span::before {
  display: inline-block;
  width: 20px;
  height: 3px;
  margin: 0 7px 3px 0;
  background: var(--chart-neutral-1);
  content: '';
}

.syd-line-chart .syd-line-key-ochre::before { background: var(--chart-1); }
.syd-line-chart .syd-line-key-blue::before { background: var(--chart-2); }
.syd-line-chart .syd-line-key-red::before { background: var(--chart-negative); }
.syd-line-chart .syd-line-key-gray::before { background: var(--chart-neutral-3); }
</style>
