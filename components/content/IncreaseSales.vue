<template>
  <div
    ref="container"
    style="position: relative; width: 100%; max-width: 800px"
    class="mb-9"
  >
    <img
      src="/bitnetmarket/increase-sales.png"
      alt="افزایش فروش"
      style="width: 100%; height: auto"
      class="rounded-lg"
    />
    <span
      ref="text"
      :style="{
        position: 'absolute',
        top: '47%',
        left: '50%',
        transform: 'translate(-50%, -50%)',
        height: 'auto',
        filter: 'blur(0.7px) drop-shadow(1px 1px 2px rgba(255, 255, 255, 0.4))',
        fontSize: fontSize + 'rem',
        whiteSpace: 'nowrap',
      }"
      class="text-white tracking-wide"
    >
      آنالیز فروش
    </span>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const container = ref(null);
const fontSize = ref(1); // default font size in rem

const updateFontSize = () => {
  if (container.value) {
    const baseFontSize = 16; // default base font size in px
    const newSize = (container.value.clientWidth * 0.08) / baseFontSize;
    fontSize.value = newSize;
  }
};

onMounted(() => {
  updateFontSize();
  window.addEventListener("resize", updateFontSize);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", updateFontSize);
});
</script>
