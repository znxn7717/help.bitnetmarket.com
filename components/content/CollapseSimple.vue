<template>
  <UiCollapsible>
    <UiCollapsibleTrigger
      :class="[
        'flex justify-between items-center cursor-pointer border rounded-lg w-full my-1 hover:bg-muted',
        { 'bg-muted': isExpand },
      ]"
      style="padding: 0.75rem 1.25rem"
      @click="toggleStatus()"
    >
      <div
        :style="{
          color: isExpand ? 'hsl(var(--primary))' : 'inherit',
        }"
      >
        <ContentSlot
          :use="$slots.title"
          unwrap="p"
          :style="{
            color: isExpand ? 'hsl(var(--primary))' : 'inherit',
          }"
        />
      </div>
      <Icon
        name="mingcute:down-line"
        :style="{
          fontSize: '1.25rem',
          minWidth: '1.25rem',
          marginRight: '1.25rem',
          transform: isExpand ? 'rotate(180deg)' : 'rotate(0deg)',
          color: isExpand ? 'hsl(var(--primary))' : 'inherit',
          transition: 'transform .35s',
        }"
      />
    </UiCollapsibleTrigger>
    <UiCollapsibleContent
      :class="{ border: isExpand, 'bg-muted': isExpand }"
      style="border-radius: var(--radius); padding: 0 1.25rem"
    >
      <div
        :style="{
          padding: isExpand ? padding : '0',
          transition: 'padding .35s linear',
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

const isExpand = ref(false);
const padding = ref("0 0");
const props = defineProps<{ id: string }>();

function toggleStatus() {
  if (!isExpand.value) {
    isExpand.value = true;
    nextTick(() => {
      requestAnimationFrame(() => {
        padding.value = "0.75rem 0";
      });
    });
  } else {
    isExpand.value = false;
    padding.value = "0";
  }
}
</script>