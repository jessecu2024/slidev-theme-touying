<script setup lang="ts">
withDefaults(defineProps<{
  src: string
  alt?: string
  fit?: 'cover' | 'contain' | 'fill' | 'scale-down'
  position?: string
  caption?: string
  radius?: 'none' | 'sm' | 'md' | 'lg'
}>(), {
  alt: '',
  fit: 'cover',
  position: 'center',
  radius: 'md',
})
</script>

<template>
  <figure class="syd-image-frame" :class="`syd-image-radius-${radius}`">
    <img
      :src="src"
      :alt="alt"
      :style="{ objectFit: fit, objectPosition: position }"
    >
    <figcaption v-if="caption">{{ caption }}</figcaption>
  </figure>
</template>

<style scoped>
.syd-image-frame {
  display: flex;
  width: 100%;
  height: 100%;
  min-width: 0;
  min-height: 0;
  margin: 0;
  flex-direction: column;
}

.syd-image-frame img {
  display: block;
  width: 100%;
  min-width: 0;
  min-height: 0;
  flex: 1;
}

.syd-image-radius-none img { border-radius: 0; }
.syd-image-radius-sm img { border-radius: var(--radius-sm); }
.syd-image-radius-md img { border-radius: var(--radius-md); }
.syd-image-radius-lg img { border-radius: var(--radius-lg); }

.syd-image-frame figcaption {
  margin-top: var(--space-2);
  color: var(--text-muted);
  font-size: 13px;
  line-height: 1.25;
}
</style>
