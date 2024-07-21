<template>
  <!-- ltr -->
  <ul
    v-if="direction === 'ltr'"
    class="py-2.5"
    :class="[level > 0 && 'border-l']"
  >
    <template v-for="link in links" :key="link._id">
      <LayoutAsideTreeItem :link="link" :level="level" />
    </template>
  </ul>

  <!-- rtl -->
  <ul
    v-if="direction === 'rtl'"
    class="py-2.5"
    :class="[level > 0 && 'border-r']"
  >
    <template v-for="link in links" :key="link._id">
      <LayoutAsideTreeItem :link="link" :level="level" />
    </template>
  </ul>
</template>

<script setup lang="ts">
import type { NavItem } from '@nuxt/content';

defineProps<{
  links: NavItem[];
  level: number;
}>();
const { direction } = useConfig().value.theme;
</script>
