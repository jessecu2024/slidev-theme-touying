<template>
  <div class="slidev-layout focus">
    <div>
      <slot />
    </div>
  </div>
</template>

<style>
.tou-preset-studio .slidev-layout.focus {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 78px 84px;
  box-sizing: border-box;
  text-align: left;
  background: var(--studio-ink) !important;
  font-size: 38px;
  font-weight: 650;
  letter-spacing: -0.04em;
  color: var(--slidev-theme-neutralLightest) !important;

  &::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 12px;
    height: 100%;
    background: var(--slidev-theme-primary);
  }

  &::after {
    content: 'STUDIO';
    position: absolute;
    right: 62px;
    top: 50px;
    color: var(--slidev-theme-secondary);
    font-size: 12px;
    font-weight: 760;
    letter-spacing: 0.22em;
  }

  & > div {
    width: 72%;
  }

  & > p, & > h1 {
    width: 72%;
  }
}
</style>
