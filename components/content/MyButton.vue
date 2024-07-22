<template>
  <section
    class="flex w-full items-center justify-center space-x-4 py-4 md:pb-10 gap-4"
  >
    <NuxtLink
      v-for="(action, i) in actions"
      :key="i"
      :to="action.to"
      :target="action.target"
    >
      <UiButton :variant="action.variant">
        <Icon v-if="action.rightIcon" :name="action.rightIcon" class="ml-1" />
        {{ action.name }}
        <Icon v-if="action.leftIcon" :name="action.leftIcon" class="mr-1" />
      </UiButton>
    </NuxtLink>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  actions: [
    {
      name: string;
      leftIcon?: string;
      rightIcon?: string;
      variant?:
        | "default"
        | "link"
        | "destructive"
        | "outline"
        | "secondary"
        | "ghost";
      to: string;
      target?: string;
    }
  ];
}>();
</script>
