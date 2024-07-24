<template>
  <button
    v-if="$slots.details && !detailsVisible"
    class="text-primary mx-1"
    @click="showDetails"
  >
    ادامه مطلب ...
  </button>
  <ContentSlot v-if="detailsVisible" :use="$slots.details" unwrap="p" />
</template>

<script setup lang="ts">
import { ref, nextTick } from "vue";

const detailsVisible = ref(false);

function showDetails() {
  detailsVisible.value = true;
}
</script>
