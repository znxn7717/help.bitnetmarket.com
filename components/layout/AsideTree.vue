<template>
  <!-- ltr -->
  <ul
    class="py-2.5"
    :class="[level > 0 && 'border-l']"
    v-if="direction == 'ltr'"
  >
    <template v-for="link in links" :key="link._id">
      <LayoutAsideTreeItem :link="link" :level="level" />
    </template>
  </ul>

  <!-- rtl -->
  <ul
    class="py-2.5"
    :class="[level > 0 && 'border-r']"
    v-if="direction == 'rtl'"
  >
    <template v-for="link in links" :key="link._id">
      <LayoutAsideTreeItem :link="link" :level="level" />
    </template>
  </ul>
</template>

<script setup lang="ts">
import type { NavItem } from "@nuxt/content";

const { direction } = useConfig().value.theme;
defineProps<{
  links: NavItem[];
  level: number;
}>();
</script>
