<template>
  <div>
    <!-- ltr -->
    <NuxtLink
      v-if="logo.light && logo.dark && direction == 'ltr'"
      to="/"
      class="flex"
    >
      <!-- <NuxtImg v-if="showIcon" :src="icon.light" class="dark:hidden h-7 mr-1" />
      <NuxtImg
        v-if="showIcon"
        :src="icon.dark"
        class="hidden dark:block h-7 mr-1"
      /> -->
      <LayoutHeaderIcon v-if="showIcon" class="ml-1" />
      <NuxtImg :src="logo.light" class="dark:hidden h-7" />
      <NuxtImg :src="logo.dark" class="hidden dark:block h-7" />
      <span v-if="showTitle && title" class="self-center font-bold ml-3">
        {{ title }}
      </span>
    </NuxtLink>

    <!-- rtl -->
    <NuxtLink
      v-if="logo.light && logo.dark && direction == 'rtl'"
      to="/"
      class="flex items-center"
      dir="rtl"
    >
      <NuxtImg :src="logo.light" class="dark:hidden h-7" />
      <NuxtImg :src="logo.dark" class="hidden dark:block h-7" />
      <LayoutHeaderIcon v-if="showIcon" class="mr-1" />
      <span v-if="showTitle && title" class="self-center font-bold mr-3">
        {{ title }}
      </span>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
const { icon, showIcon, logo, title, showTitle } = useConfig().value.header;
const { direction } = useConfig().value.theme;
</script>
