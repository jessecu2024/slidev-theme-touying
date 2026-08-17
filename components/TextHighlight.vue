<script setup lang="ts">
withDefaults(defineProps<{
  color?: 'red' | 'green'
}>(), {
  color: 'red',
})
</script>

<template>
  <span class="tou-text-highlight" :class="`is-${color}`"><slot /></span>
</template>

<style scoped>
.tou-text-highlight {
  display: inline;
  padding: 0.08em 0.22em;
  border-radius: 0.18em;
  box-decoration-break: clone;
  -webkit-box-decoration-break: clone;
  font-weight: 700;
}

.tou-text-highlight.is-red {
  background: #fbe9e7;
  color: #b42318;
  box-shadow: inset 0 -2px 0 #b42318;
}

.tou-text-highlight.is-green {
  background: #e6f4ec;
  color: #18794e;
  box-shadow: inset 0 -2px 0 #18794e;
}
</style>
