<template>
  <!-- ltr -->
  <li
    role="presentation"
    aria-hidden="true"
    :class="cn('[&>svg]:size-3.5', props.class)"
    v-if="direction == 'ltr'"
  >
    <slot>
      <ChevronRight />
    </slot>
  </li>

  <!-- rtl -->
  <li
    role="presentation"
    aria-hidden="true"
    :class="cn('[&>svg]:size-3.5', props.class)"
    v-if="direction == 'rtl'"
  >
    <slot>
      <ChevronRight class="rotate-180" />
    </slot>
  </li>
</template>

<script lang="ts" setup>
import type { HTMLAttributes } from "vue";
import { ChevronRight } from "lucide-vue-next";
import { cn } from "@/lib/utils";

const { direction } = useConfig().value.theme;
const props = defineProps<{
  class?: HTMLAttributes["class"];
}>();
</script>
