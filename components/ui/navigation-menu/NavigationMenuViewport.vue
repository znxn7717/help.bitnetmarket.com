<template>
  <!-- ltr -->
  <div
    v-if="direction === 'ltr'"
    class="absolute left-0 top-full flex justify-center"
  >
    <NavigationMenuViewport
      v-bind="forwardedProps"
      :class="
        cn(
          'origin-top-center relative mt-1.5 h-[--radix-navigation-menu-viewport-height] w-full overflow-hidden rounded-md border bg-popover text-popover-foreground shadow-lg data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-90 md:w-[--radix-navigation-menu-viewport-width]',
          props.class,
        )
      "
    />
  </div>

  <!-- rtl -->
  <div
    v-if="direction === 'rtl'"
    class="absolute right-0 top-full flex justify-center"
    dir="rtl"
  >
    <NavigationMenuViewport
      v-bind="forwardedProps"
      :class="
        cn(
          'origin-top-center relative mt-1.5 h-[--radix-navigation-menu-viewport-height] w-full overflow-hidden rounded-md border bg-popover text-popover-foreground shadow-lg data-[state=open]:animate-in data-[state=closed]:animate-out data-[state=closed]:zoom-out-95 data-[state=open]:zoom-in-90 md:w-[--radix-navigation-menu-viewport-width]',
          props.class,
        )
      "
    />
  </div>
</template>

<script setup lang="ts">
import { type HTMLAttributes, computed } from 'vue';
import {
  NavigationMenuViewport,
  type NavigationMenuViewportProps,
  useForwardProps,
} from 'radix-vue';
import { cn } from '@/lib/utils';

const props = defineProps<
  NavigationMenuViewportProps & { class?: HTMLAttributes['class'] }
>();
const { direction } = useConfig().value.theme;
const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});

const forwardedProps = useForwardProps(delegatedProps);
</script>
