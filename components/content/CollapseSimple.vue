<template>
  <UiCollapsible>
    <UiCollapsibleTrigger
      :class="[
        'flex justify-between items-center cursor-pointer w-full mb-1 shadow-sm shadow-muted px-3 pt-1 rounded-lg',
      ]"
      @click="toggleStatus()"
    >
      <div
        :style="{
          color: isExpand ? 'hsl(var(--primary))' : 'inherit',
        }"
        dir="rtl"
      >
        <slot
          :style="{
            color: isExpand ? 'hsl(var(--primary))' : 'inherit',
          }"
          dir="rtl"
        />
      </div>
      <Icon
        name="mingcute:left-line"
        :style="{
          fontSize: '1.25rem',
          minWidth: '1.25rem',
          marginRight: '1.25rem',
          transform: isExpand ? 'rotate(-90deg)' : 'rotate(0deg)',
          color: isExpand ? 'hsl(var(--primary))' : 'inherit',
          transition: 'transform .35s',
        }"
      />
    </UiCollapsibleTrigger>
    <UiCollapsibleContent
      :class="[
        'text-justify',
        { border: isExpand },
        { 'bg-muted/50': isExpand },
        { 'bg-primary/10': isExpand && $slots.detail },
      ]"
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
        <ContentSlot :use="$slots.detail" unwrap="p" />
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