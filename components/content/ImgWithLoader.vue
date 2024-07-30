<template>
  <div style="position: relative; width: 100%; max-width: 800px">
    <img
      v-if="imageLoaded"
      :src="props.src"
      :alt="props.alt"
      style="width: 100%; height: auto"
      class="rounded-lg"
    />
    <div v-else>
      <Skeleton class="h-[12rem]" />
      <DNALoader
        style="
          position: absolute;
          margin: 0;
          top: 15%;
          left: 50%;
          transform: translate(-50%, -50%);
          width: 98%;
        "
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

const props = defineProps<{ src: string; alt: string }>();

console.log(props.src);

const imageLoaded = ref(false);

onMounted(() => {
  imageLoaded.value = true;
});
</script>