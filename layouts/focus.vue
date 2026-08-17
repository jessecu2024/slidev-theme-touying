<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import HarbourFocus from '../themes/harbour/layouts/focus.vue'
import SandstoneFocus from '../themes/sandstone/layouts/focus.vue'
import StudioFocus from '../themes/studio/layouts/focus.vue'
import SydneyFocus from '../themes/sydney/layouts/focus.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() =>
  config.value.preset === 'sandstone'
    ? SandstoneFocus
    : config.value.preset === 'studio'
      ? StudioFocus
      : config.value.preset === 'sydney'
        ? SydneyFocus
        : HarbourFocus,
)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
