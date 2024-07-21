<template>
  <!-- ltr -->
  <ul v-if="direction === 'ltr'" :class="[level !== 0 && 'pl-4']">
    <li v-for="link in links" :key="link.id" class="pt-2">
      <NuxtLink
        :to="`#${link.id}`"
        class="text-muted-foreground hover:text-primary transition-all"
        :class="[activeHeadings.includes(link.id) && 'text-primary']"
      >
        {{ link.text }}
      </NuxtLink>
      <TocTree v-if="link.children" :links="link.children" :level="level + 1" />
    </li>
  </ul>

  <!-- rtl -->
  <ul v-if="direction === 'rtl'" :class="[level !== 0 && 'pr-4']">
    <li v-for="link in links" :key="link.id" class="pt-2">
      <NuxtLink
        :to="`#${link.id}`"
        class="text-muted-foreground hover:text-primary transition-all"
        :class="[activeHeadings.includes(link.id) && 'text-primary']"
      >
        {{ link.text }}
      </NuxtLink>
      <TocTree v-if="link.children" :links="link.children" :level="level + 1" />
    </li>
  </ul>
</template>

<script setup lang="ts">
import type { TocLink } from '@nuxt/content';

defineProps<{
  links: TocLink[];
  level: number;
}>();
const { direction } = useConfig().value.theme;
const { activeHeadings, updateHeadings } = useScrollspy();

onMounted(() =>
  updateHeadings([
    ...document.querySelectorAll('.docs-content h1'),
    ...document.querySelectorAll('.docs-content h2'),
    ...document.querySelectorAll('.docs-content h3'),
    ...document.querySelectorAll('.docs-content h4'),
  ]),
);
</script>
