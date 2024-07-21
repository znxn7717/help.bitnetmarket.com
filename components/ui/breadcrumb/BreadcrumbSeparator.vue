<template>
  <!-- ltr -->
  <li
    v-if="direction === 'ltr'"
    role="presentation"
    aria-hidden="true"
    :class="cn('[&>svg]:size-3.5', props.class)"
  >
    <slot>
      <ChevronRight />
    </slot>
  </li>

  <!-- rtl -->
  <li
    v-if="direction === 'rtl'"
    role="presentation"
    aria-hidden="true"
    :class="cn('[&>svg]:size-3.5', props.class)"
  >
    <slot>
      <ChevronRight class="rotate-180" />
    </slot>
  </li>
</template>

<script lang="ts" setup>
import type { HTMLAttributes } from 'vue';
import { ChevronRight } from 'lucide-vue-next';
import { cn } from '@/lib/utils';

const props = defineProps<{
  class?: HTMLAttributes['class'];
}>();
const { direction } = useConfig().value.theme;
</script>
