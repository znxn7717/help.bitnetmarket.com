<template>
  <!-- ltr -->
  <UiSheet v-model:open="open" v-if="direction == 'ltr'">
    <UiSheetTrigger as-child>
      <UiButton variant="ghost" size="icon" class="md:hidden">
        <Icon name="lucide:menu" size="18" />
      </UiButton>
    </UiSheetTrigger>
    <UiSheetContent side="left" class="pr-0">
      <LayoutHeaderLogo />
      <LayoutAside is-mobile />
    </UiSheetContent>
  </UiSheet>

  <!-- rtl -->
  <UiSheet v-model:open="open" v-if="direction == 'rtl'">
    <UiSheetTrigger as-child>
      <UiButton variant="ghost" size="icon" class="md:hidden">
        <Icon name="lucide:menu" size="18" />
      </UiButton>
    </UiSheetTrigger>
    <UiSheetContent side="right" class="pl-0">
      <LayoutHeaderLogo />
      <LayoutAside is-mobile />
    </UiSheetContent>
  </UiSheet>
</template>

<script setup lang="ts">
const { direction } = useConfig().value.theme;
const open = ref(false);
</script>
