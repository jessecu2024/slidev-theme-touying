<script setup lang="ts">
import SydneyCallout from '../themes/sydney/components/Callout.vue'
defineOptions({ inheritAttrs: false })
</script>
<template><SydneyCallout v-bind="$attrs"><slot /></SydneyCallout></template>
