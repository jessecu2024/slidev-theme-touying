<script setup lang="ts">
import { computed } from 'vue'
import { useTouyingConfig } from '../composables/useTouyingConfig'
import DewdropSection from '../themes/dewdrop/layouts/section.vue'
import NewSection from '../themes/new/layouts/section.vue'
import UniversitySection from '../themes/university/layouts/section.vue'
import SimpleSection from '../themes/simple/layouts/section.vue'
import SydneySection from '../themes/sydney/layouts/section.vue'

defineOptions({ inheritAttrs: false })
const config = useTouyingConfig()
const component = computed(() =>
  config.value.preset === 'new'
    ? NewSection
    : config.value.preset === 'university'
    ? UniversitySection
    : config.value.preset === 'simple' || config.value.preset === 'simple-serif'
      ? SimpleSection
      : config.value.preset === 'sydney'
        ? SydneySection
        : DewdropSection,
)
</script>

<template>
  <component :is="component" v-bind="$attrs">
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </component>
</template>
