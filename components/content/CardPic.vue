<template>
  <!-- rtl -->
  <div v-if="direction === 'rtl'" class="group-has-[div]:mt-0">
    <NuxtLink :to="to" :target="target">
      <UiCard
        class="transition-all relative h-full bg-white/10"
        :class="[to && 'hover:bg-muted']"
      >
        <UiCardHeader class="pt-0 px-0 overflow-hidden rounded-t-lg">
          <ContentSlot :use="$slots.img" unwrap="p" />
          <div>
            <div
              class="text-sm text-primary bg-primary/10 border border-primary px-3 py-0.5 mr-6 mt-3 rounded-lg inline-block"
            >
              {{ badge }}
            </div>
          </div>
        </UiCardHeader>
        <UiCardContent v-if="title || icon || footer">
          <div>
            <div class="flex flex-row my-3">
              <Icon v-if="icon" class="ml-2" :name="icon" size="24" />
              <UiCardTitle v-if="title">
                {{ title }}
              </UiCardTitle>
            </div>
          </div>
          <div class="text-muted-foreground">
            <ContentSlot :use="$slots.content" unwrap="p" />
            <ContentSlot unwrap="p" />
          </div>
        </UiCardContent>
        <UiCardFooter v-if="footer" class="justify-end text-muted-foreground">
          {{ footer }}
        </UiCardFooter>
      </UiCard>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  title?: string;
  footer?: string;
  content?: string;
  to?: string;
  target?: string;
  icon?: string;
  badge?: string;
}>();
const { direction } = useConfig().value.theme;
</script>


<style scoped>
.footer-left {
  display: flex;
  justify-content: flex-start;
  align-items: center; /* To vertically center the content */
  width: 100%; /* Ensure it takes the full width */
}
</style>