<template>
  <div>
    <header
      class="flex items-center gap-2 p-2 hover:scale-[101%] transition cursor-pointer"
    >
      <Logo />
      <p class="font-bold text-black">Nuxt-Finance</p>
    </header>
    <div class="px-4 grow">
      <div class="grid gap-4">
        <NuxtLink
          :to="item.path"
          class="flex items-center gap-2 px-2 hover:bg-neutral-100 py-1 transition rounded cursor-pointer"
          v-for="(item, index) in items"
          :key="index"
        >
          <Icon v-if="item.icon" size="20" :name="item.icon" />

          <span class="">{{ item.title }}</span>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const items = ref([
  {
    title: "OverView",
    path: "/",
    icon: "ri:dashboard-line",
  },
  {
    title: "Transactions",
    path: "/transactions",
    icon: "bx:transfer",
  },
  {
    title: "Account",
    path: "/account",
    icon: "mdi:account-circle-outline",
  },
  {
    title: "Contacts",
    path: "/contacts",
    icon: "basil:contacts-solid",
  },
  {
    title: "Settings",
    path: "/settings",
    icon: "octicon:gear-16",
  },
]);
</script>

<style scoped></style>
