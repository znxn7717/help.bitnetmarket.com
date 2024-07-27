<template>
  <div
    :class="cn(alertVariants({ variant }), props.class, 'bg-muted/50')"
    role="alert"
  >
    <slot />
  </div>
</template>

<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import { type AlertVariants, alertVariants } from ".";
import { cn } from "@/lib/utils";

const props = defineProps<{
  class?: HTMLAttributes["class"];
  variant?: AlertVariants["variant"];
}>();
</script>
