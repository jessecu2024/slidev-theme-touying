<script setup lang="ts">
/**
 * Sandstone section divider with an editorial left alignment.
 */
import TitleRenderer from '#slidev/title-renderer'
import Footer from '../components/Footer.vue'
import ProgressBar from '../components/ProgressBar.vue'

</script>

<template>
  <div class="slidev-layout section uni-section">
    <div class="uni-section-inner">
      <div class="uni-section-kicker">Institutional brief</div>
      <div class="uni-section-title">
        <TitleRenderer class="tou-title" :no="$page" />
      </div>
      <div class="uni-section-bar">
        <ProgressBar />
      </div>
      <div class="uni-section-content">
        <slot />
      </div>
    </div>
    <Footer />
  </div>
</template>

<style>
.tou-preset-sandstone .slidev-layout.section.uni-section {
  width: 100%;
  height: 100%;
  position: relative;
  background: var(--sandstone-wash);
  overflow: hidden;
  padding: 0;

  .uni-section-inner {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 48px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    padding: 0 11%;
    gap: 18px;
  }

  .uni-section-kicker {
    color: var(--slidev-theme-primary);
    font-size: 13px;
    font-weight: 750;
    letter-spacing: 0.18em;
    text-transform: uppercase;
  }

  .uni-section-title {
    font-size: 3.1em;
    font-weight: 720;
    color: var(--sandstone-ink);
    letter-spacing: -0.055em;
    line-height: 1;
    width: 76%;
  }

  .uni-section-bar {
    width: 54%;
  }

  .uni-section-content {
    width: 62%;
    color: var(--sandstone-muted);

    h1 {
      display: none;
    }
  }
}
</style>
