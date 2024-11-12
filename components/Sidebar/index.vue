<script setup lang="ts">
const open = ref(true);
</script>

<style scoped></style>

<template>
  <div class="relative">
    <div class="flex lg:hidden z-50 items-center justify-between h-full p-4">
      <Logo />
      <Icon
        class="z-50 cursor-pointer left-2 top-2"
        size="30"
        name="humbleicons:bars"
        @click="open = true"
      />
      <div
        v-if="open"
        class="absolute top-0 left-0 z-50 w-full h-screen bg-white"
      >
        <Icon
          class="z-50 absolute cursor-pointer right-4 top-4"
          size="30"
          name="material-symbols:close"
          @click="open = false"
        />
        <SidebarMenu />
      </div>
    </div>

    <div
      class="hidden lg:flex w-[250px] h-screen flex-col justify-between border-r"
    >
      <SidebarMenu />
      <div>user Item</div>
    </div>
  </div>
</template>
