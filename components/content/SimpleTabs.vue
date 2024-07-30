<template>
  <div class="flex justify-center flex-wrap h-auto bg-transparent gap-2 p-1">
    <NuxtLink to="/terms-of-use">
      <div
        class="w-48 flex flex-col items-center justify-center whitespace-nowrap px-3 py-1.5 text-xl shadow-sm rounded-lg hover:bg-muted border border-primary bg-muted text-primary"
      >
        <Icon name="octicon:law-16" size="24" class="mb-1 text-2xl" />
        <span>شرایط و مقررات مارکت</span>
      </div>
    </NuxtLink>
    <NuxtLink to="/getting-started/seller">
      <div
        class="w-48 flex flex-col items-center justify-center whitespace-nowrap px-3 py-1.5 text-xl shadow-sm rounded-lg hover:bg-muted"
      >
        <Icon name="hugeicons:bitcoin-store" size="24" class="mb-1 text-2xl" />
        <span>راهنمای فروشنده</span>
      </div>
    </NuxtLink>
    <NuxtLink to="/getting-started/customer">
      <div
        class="w-48 flex flex-col items-center justify-center whitespace-nowrap px-3 py-1.5 text-xl shadow-sm rounded-lg hover:bg-muted"
      >
        <Icon
          name="hugeicons:bitcoin-shopping"
          size="24"
          class="mb-1 text-2xl"
        />
        <span>راهنمای مشتری</span>
      </div>
    </NuxtLink>
  </div>
</template>