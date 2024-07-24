<template>
  <UiCollapsible>
    <UiCollapsibleTrigger
      class="flex justify-between items-center cursor-pointer border rounded-lg w-full my-1"
      style="padding: 0.75rem 1.25rem"
      @click="toggleStatus"
    >
      <div
        :style="{
          color: status === 'open' ? 'hsl(var(--primary))' : 'inherit',
        }"
      >
        <ContentSlot :use="$slots.title" unwrap="p" />
      </div>
      <Icon
        name="mingcute:down-line"
        size="20"
        :style="{
          transform: status === 'open' ? 'rotate(180deg)' : 'rotate(0deg)',
          color: status === 'open' ? 'hsl(var(--primary))' : 'inherit',
        }"
      />
    </UiCollapsibleTrigger>
    <UiCollapsibleContent
      v-if="$slots.description"
      :id="id"
      :class="{ border: status === 'open' }"
      style="border-radius: var(--radius); padding: 0 1.25rem"
    >
      <div
        :style="{
          paddingTop: status === 'open' ? paddingTop : '0',
          paddingBottom: status === 'open' ? paddingBottom : '0',
          transition: 'padding-top .35s linear, padding-bottom .35s linear',
          overflow: 'hidden',
        }"
      >
        <ContentSlot :use="$slots.description" unwrap="p" />
      </div>
    </UiCollapsibleContent>
  </UiCollapsible>
</template>

<script setup lang="ts">
import { ref, nextTick } from "vue";

const status = ref("closed");
const paddingTop = ref("0");
const paddingBottom = ref("0");

function toggleStatus() {
  if (status.value === "closed") {
    status.value = "open";
    nextTick(() => {
      requestAnimationFrame(() => {
        paddingTop.value = "0.75rem";
        paddingBottom.value = "0.75rem";
      });
    });
  } else {
    status.value = "closed";
    paddingTop.value = "0";
    paddingBottom.value = "0";
  }
}
defineProps<{
  id: string;
}>();
</script>
