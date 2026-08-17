<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import HarbourSection from '../themes/harbour/layouts/section.vue'
import SandstoneSection from '../themes/sandstone/layouts/section.vue'
import StudioSection from '../themes/studio/layouts/section.vue'
import SydneySection from '../themes/sydney/layouts/section.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() =>
  config.value.preset === 'sandstone'
    ? SandstoneSection
    : config.value.preset === 'studio'
      ? StudioSection
      : config.value.preset === 'sydney'
        ? SydneySection
        : HarbourSection,
)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
