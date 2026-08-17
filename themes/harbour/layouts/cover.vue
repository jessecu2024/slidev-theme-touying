<script setup lang="ts">
/**
 * cover layout — Title slide
 *
 * White, left-aligned cover with a blue horizon rule.
 */
import { useSlideContext } from '@slidev/client'

const { $slidev, $frontmatter } = useSlideContext()
</script>

<template>
  <div class="slidev-layout cover">
    <div class="cover-inner">
      <div class="cover-kicker">Harbour presentation system</div>

      <div class="cover-title-box">
        <div class="cover-title">
          <slot name="title">
            {{ $slidev.configs.title }}
          </slot>
        </div>
        <div v-if="$frontmatter.subtitle" class="cover-subtitle">
          <slot name="subtitle">{{ $frontmatter.subtitle }}</slot>
        </div>
      </div>

      <div class="cover-meta">
        <div v-if="$slidev.configs.author" class="cover-author">
          <slot name="author">{{ $slidev.configs.author }}</slot>
        </div>
      </div>

      <div v-if="$slots.default" class="cover-extra">
        <slot />
      </div>
    </div>
  </div>
</template>

<style>
.tou-preset-harbour .slidev-layout.cover {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  height: 100%;
  padding: 72px 82px;
  background: #ffffff;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 18px;
    height: 100%;
    background: var(--slidev-theme-primary);
  }

  &::after {
    content: '';
    position: absolute;
    right: 0;
    bottom: 78px;
    width: 32%;
    height: 7px;
    background: var(--slidev-theme-secondary);
  }

  .cover-inner {
    width: 72%;
    padding: 0;
    text-align: left;
    box-sizing: border-box;
  }

  .cover-kicker {
    color: var(--slidev-theme-primary);
    font-size: 0.66em;
    font-weight: 700;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    margin-bottom: 1.4em;
  }

  .cover-title-box {
    border-top: 2px solid var(--harbour-ink);
    padding: 28px 0 26px;
    margin-bottom: 0;
  }

  .cover-title {
    font-size: 3.05em;
    font-weight: 720;
    color: var(--harbour-ink);
    letter-spacing: -0.055em;
    line-height: 0.98;
  }

  .cover-subtitle {
    font-size: 1.08em;
    color: var(--harbour-muted);
    line-height: 1.35;
    margin-top: 18px;
    max-width: 32em;
  }

  .cover-meta {
    font-size: 0.74em;
    color: var(--harbour-muted);
    display: flex;
    flex-direction: row;
    gap: 1.5em;
    align-items: baseline;
  }

  .cover-author {
    font-size: 1em;
    font-weight: 650;
    color: var(--harbour-ink);
    line-height: 1.4;
  }

  .cover-extra {
    margin-top: 0.8em;
    font-size: 0.72em;
    color: var(--harbour-muted);

    h1 {
      display: none;
    }
  }
}
</style>
