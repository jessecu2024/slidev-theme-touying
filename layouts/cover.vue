<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import HarbourCover from '../themes/harbour/layouts/cover.vue'
import SandstoneCover from '../themes/sandstone/layouts/cover.vue'
import StudioCover from '../themes/studio/layouts/cover.vue'
import SydneyCover from '../themes/sydney/layouts/cover.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() =>
  config.value.preset === 'sandstone'
    ? SandstoneCover
    : config.value.preset === 'studio'
      ? StudioCover
      : config.value.preset === 'sydney'
        ? SydneyCover
        : HarbourCover,
)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
