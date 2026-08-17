<script setup lang="ts">
import SydneyCaption from '../themes/sydney/components/Caption.vue'
defineOptions({ inheritAttrs: false })
</script>
<template><SydneyCaption v-bind="$attrs"><slot /></SydneyCaption></template>
