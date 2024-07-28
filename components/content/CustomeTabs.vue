<template>
  <UiTabs v-model="currentTab">
    <!-- <img
      v-if="currentTab === 'پیگیری سفارش'"
      src="/bitnetmarket/order-tracking.png"
      alt="پیگیری سفارش"
      class="rounded-lg my-5"
      style="width: 100%; height: auto; display: block"
    /> -->
    <order-tracking v-if="currentTab === 'پیگیری سفارش'" />
    <problem-and-return v-if="currentTab === 'مشکل و مرجوعی'" />
    <div class="flex flex-col mt-10">
      <div class="flex justify-center">
        <UiTabsList
          dir="rtl"
          class="flex flex-wrap h-auto bg-transparent gap-2"
        >
          <UiTabsTrigger
            v-for="(slot, i) in slots.default?.() ?? []"
            :key="`${i}${label(slot.props)}`"
            :value="label(slot.props)"
            class="w-48 flex flex-col items-center text-xl hover:bg-muted shadow-sm data-[state=active]:bg-muted data-[state=active]:border data-[state=active]:border-primary data-[state=active]:text-primary rounded-lg"
          >
            <Icon
              v-if="icon(slot?.props)"
              :name="icon(slot?.props)"
              class="mb-1 text-2xl"
            />
            {{ label(slot.props) }}
          </UiTabsTrigger>
        </UiTabsList>
      </div>

      <UiTabsContent
        v-for="(slot, i) in slots.default?.() ?? []"
        :key="`${i}${label(slot.props)}`"
        :value="label(slot.props)"
        dir="rtl"
        class="mt-10"
      >
        <component :is="slot" />
      </UiTabsContent>
    </div>
  </UiTabs>
</template>

<script setup lang="ts">
import { ref, watch, getCurrentInstance } from "vue";
import { useRouter } from "vue-router";

withDefaults(
  defineProps<{
    padded?: boolean;
  }>(),
  {
    padded: true,
  }
);

const instance = getCurrentInstance();
const slots = instance?.slots;
const router = useRouter();

function icon(props: any) {
  return props?.icon;
}

function label(props: any) {
  return props?.label;
}

// Track the current tab value
const initialTab = label((slots.default?.() ?? [])[1]?.props);
const currentTab = ref(initialTab);

// Watch for changes to currentTab and handle redirection
watch(currentTab, (newTab) => {
  if (newTab === "شرایط و مقررات مارکت") {
    router.push("/terms-of-use");
  }
});
</script>
