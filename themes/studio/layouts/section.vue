<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $route, $page } = useSlideContext()
</script>

<template>
  <div class="slidev-layout section">
    <div class="spl-section-index">{{ String($page).padStart(2, '0') }}</div>
    <div class="spl-section-title">{{ $route?.meta.slide.title }}</div>
    <div class="spl-section-rule" />
  </div>
</template>

<style>
.tou-preset-studio .slidev-layout.section {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-end;
  padding: 76px 82px 88px;
  box-sizing: border-box;
  background: #ffffff;

  .spl-section-index {
    position: absolute;
    top: 62px;
    right: 72px;
    font-size: 5.8em;
    font-weight: 760;
    line-height: 1;
    letter-spacing: -0.08em;
    color: var(--studio-lilac);
  }

  .spl-section-title {
    position: relative;
    width: 66%;
    font-size: 3.05em;
    font-weight: 760;
    color: var(--studio-ink);
    text-align: left;
    line-height: 0.98;
    letter-spacing: -0.06em;
    z-index: 1;
  }

  .spl-section-rule {
    width: 120px;
    height: 9px;
    margin-top: 26px;
    background: var(--slidev-theme-secondary);
  }
}
</style>
