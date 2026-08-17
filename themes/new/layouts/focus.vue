<template>
  <div class="slidev-layout focus new-focus">
    <div class="new-focus-body">
      <div class="new-focus-rule" />
      <slot />
    </div>
  </div>
</template>

<style>
.tou-preset-new .slidev-layout.new-focus {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 72px 82px 90px;
  box-sizing: border-box;
  text-align: center;
  background: #ffffff !important;

  .new-focus-body {
    width: min(760px, 84%);
  }

  .new-focus-rule {
    width: 64px;
    height: 5px;
    margin: 0 auto 32px;
    background: var(--slidev-theme-primary);
  }

  p,
  h1 {
    color: var(--new-ink) !important;
    font-size: 1.85em;
    font-weight: 700;
    line-height: 1.2;
    letter-spacing: -0.045em;
  }
}
</style>
