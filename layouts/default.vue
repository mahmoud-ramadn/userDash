<template>
  <div class="grid items-start lg:flex">
    <Sidebar />
    <main class="p-6 w-full">
      <slot />
    </main>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
