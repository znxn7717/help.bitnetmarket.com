<template>
  <!-- ltr -->
  <NavigationMenuTrigger
    v-if="direction === 'ltr'"
    v-bind="forwardedProps"
    :class="cn(navigationMenuTriggerStyle(), 'group', props.class)"
  >
    <slot />
    <ChevronDown
      class="relative top-px ml-1 h-3 w-3 transition duration-200 group-data-[state=open]:rotate-180"
      aria-hidden="true"
    />
  </NavigationMenuTrigger>

  <!-- rtl -->
  <NavigationMenuTrigger
    v-if="direction === 'rtl'"
    v-bind="forwardedProps"
    :class="cn(navigationMenuTriggerStyle(), 'group', props.class)"
  >
    <slot />
    <ChevronDown
      class="relative top-px mr-1 h-3 w-3 transition duration-200 group-data-[state=open]:rotate-180"
      aria-hidden="true"
    />
  </NavigationMenuTrigger>
</template>

<script setup lang="ts">
import { type HTMLAttributes, computed } from 'vue';
import {
  NavigationMenuTrigger,
  type NavigationMenuTriggerProps,
  useForwardProps,
} from 'radix-vue';
import { ChevronDown } from 'lucide-vue-next';
import { navigationMenuTriggerStyle } from '.';
import { cn } from '@/lib/utils';

const props = defineProps<
  NavigationMenuTriggerProps & { class?: HTMLAttributes['class'] }
>();

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});

const forwardedProps = useForwardProps(delegatedProps);
const { direction } = useConfig().value.theme;
</script>
