<script setup lang="ts">
import SydneyQuote from '../themes/sydney/components/Quote.vue'
defineOptions({ inheritAttrs: false })
</script>
<template><SydneyQuote v-bind="$attrs"><slot /></SydneyQuote></template>
