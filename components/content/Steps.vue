<template>
  <!-- ltr -->
  <div
    class="[&>h3]:step [&>li]:step ml-4 border-l pl-8 [counter-reset:step] [&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-12"
    v-if="direction === 'ltr'"
  >
    <slot />
  </div>

  <!-- rtl -->
  <div
    class="[&>h3]:step [&>h3]:step-rtl [&>li]:step [&>li]:step-rtl mr-4 border-r pr-8 [counter-reset:step] [&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-12"
    v-if="direction === 'rtl'"
  >
    <slot />
  </div>
</template>

<script setup lang="ts">
const config = useConfig();
const direction = config.value.theme.direction;
</script>
