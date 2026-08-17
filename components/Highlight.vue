<script setup lang="ts">
import SydneyHighlight from '../themes/sydney/components/Highlight.vue'
defineOptions({ inheritAttrs: false })
</script>
<template><SydneyHighlight v-bind="$attrs"><slot /></SydneyHighlight></template>
