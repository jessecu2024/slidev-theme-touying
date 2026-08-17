<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from './composables/useTouyingConfig'
import HarbourLayer from './themes/harbour/global-layer.vue'
import SandstoneLayer from './themes/sandstone/global-layer.vue'
import StudioLayer from './themes/studio/global-layer.vue'
import SydneyLayer from './themes/sydney/global-layer.vue'
defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() => {
  if (config.value.preset === 'harbour') return HarbourLayer
  if (config.value.preset === 'sandstone') return SandstoneLayer
  if (config.value.preset === 'studio') return StudioLayer
  if (config.value.preset === 'sydney') return SydneyLayer
  throw new Error(`Unknown preset: ${config.value.preset}`)
})
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
