<script setup lang="ts">
import SydneyLayout from '../themes/sydney/layouts/image-full.vue'
defineOptions({ inheritAttrs: false })
</script>
<template>
  <SydneyLayout v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps"><slot :name="name" v-bind="slotProps ?? {}" /></template>
  </SydneyLayout>
</template>
