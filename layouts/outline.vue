<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import HarbourOutline from '../themes/harbour/layouts/outline.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
// Harbour owns the navigation-aware outline layout.
const component = computed(() => HarbourOutline)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
