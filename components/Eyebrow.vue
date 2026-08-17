<script setup lang="ts">
import SydneyEyebrow from '../themes/sydney/components/Eyebrow.vue'
defineOptions({ inheritAttrs: false })
</script>
<template><SydneyEyebrow v-bind="$attrs"><slot /></SydneyEyebrow></template>
