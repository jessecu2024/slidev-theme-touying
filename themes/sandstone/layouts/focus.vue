<script setup lang="ts">
/**
 * Sandstone focus slide.
 */
</script>

<template>
  <div class="slidev-layout focus">
    <slot />
  </div>
</template>

<style>
.tou-preset-sandstone .slidev-layout.focus {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  background: var(--slidev-theme-secondary);
  font-size: 2.45em;
  font-weight: 650;
  line-height: 1.12;
  letter-spacing: -0.045em;
  padding: 76px 88px;
  box-sizing: border-box;
  text-align: left;

  &::before {
    content: '';
    position: absolute;
    left: 88px;
    top: 76px;
    width: 64px;
    height: 8px;
    background: var(--slidev-theme-tertiary);
  }

  &::after {
    content: 'SANDSTONE';
    position: absolute;
    right: 66px;
    bottom: 50px;
    font-size: 12px;
    font-weight: 750;
    letter-spacing: 0.2em;
    color: rgba(255, 255, 255, 0.62);
  }

  &, & p, & h1 {
    color: var(--slidev-theme-neutralLightest) !important;
  }

  & code {
    background-color: rgba(255, 255, 255, 0.18);
  }

  & > p, & > h1 {
    width: 74%;
  }
}
</style>
