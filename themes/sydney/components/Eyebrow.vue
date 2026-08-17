<script setup lang="ts">
withDefaults(defineProps<{
  color?: 'ochre' | 'blue' | 'muted' | 'charcoal'
}>(), {
  color: 'ochre',
})
</script>

<template>
  <div class="syd-eyebrow" :class="`syd-eyebrow-${color}`"><slot /></div>
</template>

<style scoped>
.syd-eyebrow {
  margin-bottom: var(--space-3);
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 750;
  letter-spacing: 0.105em;
  line-height: 1.15;
  text-transform: uppercase;
}

.syd-eyebrow-blue { color: var(--color-blue); }
.syd-eyebrow-muted { color: var(--text-muted); }
.syd-eyebrow-charcoal { color: var(--color-charcoal); }
</style>
