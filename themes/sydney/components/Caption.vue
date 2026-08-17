<script setup lang="ts">
withDefaults(defineProps<{
  align?: 'left' | 'center' | 'right'
}>(), {
  align: 'left',
})
</script>

<template>
  <div class="syd-caption" :style="{ textAlign: align }"><slot /></div>
</template>

<style scoped>
.syd-caption {
  margin-top: var(--space-2);
  color: var(--text-muted);
  font-size: 13px;
  line-height: 1.3;
}

.syd-caption :deep(p) { margin: 0; }
</style>
