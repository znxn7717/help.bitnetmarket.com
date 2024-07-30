<template>
  <div
    style="
      position: relative;
      width: 100%;
      max-width: 800px;
      filter: drop-shadow(1px 1px 1px rgb(0 0 0 / 0.05));
      margin-top: 40px;
      margin-bottom: 40px;
    "
  >
    <img
      v-if="imageLoaded"
      :src="imageSrc"
      alt="معرفی"
      class="rounded-lg"
      style="width: 100%; height: auto; display: block"
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
    <LayoutHeaderIcon
      v-if="imageLoaded"
      style="
        position: absolute;
        margin: 0;
        top: 43%;
        left: 49%;
        transform: translate(-50%, -50%);
        height: 40%;
        filter: blur(1px) drop-shadow(2px 2px 5px rgba(0, 0, 0, 0.8));
      "
    />
    <div
      v-if="imageLoaded"
      style="
        position: absolute;
        top: 90%;
        left: 50%;
        transform: translate(-50%, -50%);
        text-align: right;
        filter: blur(0.5px) drop-shadow(0.5px 0.5px 2px rgba(155, 155, 155, 1));
        color: white;
        white-space: nowrap;
        line-height: 1;
        font-family: vazirrdfdnl;
      "
      class="text-xl lg:text-2xl"
    >
      <span> بر لبه نوآوری </span>
    </div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from "vue";

const imageLoaded = ref(false);
const imageSrc = "/bitnetmarket/introduction.png";

onMounted(() => {
  imageLoaded.value = true;
});
</script>