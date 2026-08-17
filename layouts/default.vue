<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import HarbourDefault from '../themes/harbour/layouts/default.vue'
import SandstoneDefault from '../themes/sandstone/layouts/default.vue'
import StudioDefault from '../themes/studio/layouts/default.vue'
import SydneyDefault from '../themes/sydney/layouts/default.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() =>
  config.value.preset === 'sandstone'
    ? SandstoneDefault
    : config.value.preset === 'studio'
      ? StudioDefault
      : config.value.preset === 'sydney'
        ? SydneyDefault
        : HarbourDefault,
)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
