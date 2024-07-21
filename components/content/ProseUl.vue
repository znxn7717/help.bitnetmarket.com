<template>
  <!-- ltr -->
  <ul
    v-if="direction === 'ltr'"
    class="[&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-6 ml-6 list-disc [&>li:not(:first-child)]:mt-2"
  >
    <slot />
  </ul>

  <!-- rtl -->
  <ul
    v-if="direction === 'rtl'"
    class="[&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-6 mr-6 list-disc [&>li:not(:first-child)]:mt-2"
  >
    <slot />
  </ul>
</template>

<script setup lang="ts">
const { direction } = useConfig().value.theme;
</script>
