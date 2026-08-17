<script setup lang="ts">
/**
 * focus layout — Emphasis/focus slide
 *
 * Deep navy statement slide with blue and sea-glass accents.
 * No navigation, no footer. Slide counter still increments.
 */
</script>

<template>
  <div class="slidev-layout focus" style="width:100%; height:100%;">
    <div class="content">
      <slot />
    </div>
  </div>
</template>

<style>
.tou-preset-harbour .slidev-layout.focus {
  position: relative;
  background: var(--harbour-ink);
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 74px 82px;

  &::before {
    content: 'FOCUS';
    position: absolute;
    top: 68px;
    left: 82px;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 0.2em;
    color: var(--slidev-theme-secondary);
  }

  &::after {
    content: '';
    position: absolute;
    right: 0;
    bottom: 0;
    width: 32%;
    height: 12px;
    background: var(--slidev-theme-primary);
  }

  .content {
    width: 72%;
    font-size: 1.75em;
    font-weight: 620;
    color: var(--slidev-theme-neutralLightest);
    text-align: left;
    letter-spacing: -0.035em;
    line-height: 1.18;
  }

  code {
    background: rgba(255, 255, 255, 0.18);
    color: var(--slidev-theme-neutralLightest);
    border-radius: 6px;
  }
}
</style>
