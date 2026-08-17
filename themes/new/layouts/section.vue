<script setup lang="ts">
import { useSlideContext } from '@slidev/client'

const { $route } = useSlideContext()
</script>

<template>
  <div class="slidev-layout section new-section">
    <div class="new-section-body">
      <div class="new-section-kicker">SECTION</div>
      <div class="new-section-title">{{ $route?.meta.slide.title }}</div>
    </div>
  </div>
</template>

<style>
.tou-preset-new .slidev-layout.new-section {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 72px 72px 86px;
  box-sizing: border-box;
  background: #ffffff !important;

  .new-section-body {
    text-align: center;
  }

  .new-section-kicker {
    margin-bottom: 18px;
    color: var(--slidev-theme-primary);
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.16em;
  }

  .new-section-title {
    color: var(--new-ink);
    font-size: 2.2em;
    font-weight: 720;
    line-height: 1.08;
    letter-spacing: -0.05em;
  }
}
</style>
