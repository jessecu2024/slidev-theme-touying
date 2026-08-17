<script setup lang="ts">
defineProps<{
  author?: string
  role?: string
  accent?: 'ochre' | 'blue' | 'charcoal'
}>()
</script>

<template>
  <figure class="syd-quote" :class="`syd-quote-${accent || 'ochre'}`">
    <blockquote class="syd-quote-text"><slot /></blockquote>
    <figcaption v-if="author || role" class="syd-quote-attribution">
      <span v-if="author" class="syd-quote-author">{{ author }}</span>
      <span v-if="role" class="syd-quote-role">{{ role }}</span>
    </figcaption>
  </figure>
</template>

<style scoped>
.syd-quote {
  --quote-color: var(--color-primary);
  margin: 0;
}

.syd-quote-blue { --quote-color: var(--color-blue); }
.syd-quote-charcoal { --quote-color: var(--color-charcoal); }

.syd-quote-text {
  margin: 0 !important;
  padding: 0 0 0 var(--space-5) !important;
  border-left: 3px solid var(--quote-color) !important;
  color: var(--text-primary) !important;
  font-size: clamp(28px, 3.4vw, 42px);
  font-weight: 520;
  letter-spacing: -0.03em;
  line-height: 1.18;
}

.syd-quote-text :deep(p) {
  margin: 0;
}

.syd-quote-attribution {
  display: flex;
  flex-direction: column;
  gap: 2px;
  margin: var(--space-5) 0 0 calc(var(--space-5) + 3px);
  font-size: 15px;
  line-height: 1.35;
}

.syd-quote-author {
  color: var(--text-primary);
  font-weight: 700;
}

.syd-quote-role {
  color: var(--text-muted);
}
</style>
