<template>
  <aside class="tou-emphasis-box">
    <slot />
  </aside>
</template>

<style scoped>
.tou-emphasis-box {
  margin: 1.1em 0;
  padding: 0.85em 1.1em;
  border-radius: 12px;
  background: var(--slidev-theme-primary, #105ca4);
  color: #ffffff;
  font-size: 0.92em;
  font-weight: 600;
  line-height: 1.45;
}

.tou-emphasis-box :deep(p) {
  margin: 0;
}

.tou-emphasis-box :deep(strong),
.tou-emphasis-box :deep(b),
.tou-emphasis-box :deep(a) {
  color: #ffffff !important;
}
</style>
