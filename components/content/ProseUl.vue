<template>
  <!-- ltr -->
  <ul
    class="[&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-6 ml-6 list-disc [&>li:not(:first-child)]:mt-2"
    v-if="direction == 'ltr'"
  >
    <slot />
  </ul>

  <!-- rtl -->
  <ul
    class="[&:not(:first-child)]:mt-6 [&:not(:last-child)]:mb-6 mr-6 list-disc [&>li:not(:first-child)]:mt-2"
    v-if="direction == 'rtl'"
  >
    <slot />
  </ul>
</template>

<script setup lang="ts">
const { direction } = useConfig().value.theme;
</script>
