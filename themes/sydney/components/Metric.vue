<script setup lang="ts">
withDefaults(defineProps<{
  value: string | number
  label?: string
  note?: string
  accent?: 'ochre' | 'blue' | 'red' | 'charcoal'
  align?: 'left' | 'center' | 'right'
}>(), {
  accent: 'ochre',
  align: 'left',
})
</script>

<template>
  <div class="syd-metric" :class="[`syd-metric-${accent}`, `syd-metric-${align}`]">
    <div class="syd-metric-value">{{ value }}</div>
    <div v-if="label" class="syd-metric-label">{{ label }}</div>
    <div v-if="note" class="syd-metric-note">{{ note }}</div>
  </div>
</template>

<style scoped>
.syd-metric {
  --metric-color: var(--color-primary);
  min-width: 0;
}

.syd-metric-blue { --metric-color: var(--color-blue); }
.syd-metric-red { --metric-color: var(--color-red); }
.syd-metric-charcoal { --metric-color: var(--color-charcoal); }
.syd-metric-center { text-align: center; }
.syd-metric-right { text-align: right; }

.syd-metric-value {
  color: var(--metric-color);
  font-size: clamp(52px, 7vw, 84px);
  font-weight: 750;
  font-variant-numeric: tabular-nums;
  letter-spacing: -0.065em;
  line-height: 0.95;
}

.syd-metric-label {
  max-width: 24ch;
  margin-top: var(--space-3);
  color: var(--text-primary);
  font-size: 20px;
  font-weight: 600;
  line-height: 1.25;
}

.syd-metric-center .syd-metric-label { margin-right: auto; margin-left: auto; }
.syd-metric-right .syd-metric-label { margin-left: auto; }

.syd-metric-note {
  margin-top: var(--space-2);
  color: var(--text-muted);
  font-size: 15px;
  line-height: 1.3;
}
</style>
