<template>
  <div class="grid w-full gap-4">
    <header class="flex items-start justify-between">
      <div class="grow">
        <p>Hi, welcome Guilaume</p>
        <h1>Dashboard</h1>
      </div>
      <div class="bg-neutral-200 h-12 w-[120px]"></div>
    </header>

    <main class="grid gap-4">
      <Tabs default-value="account" class="w-[400px]">
        <TabsList>
          <TabsTrigger value="today"> Today </TabsTrigger>
          <TabsTrigger value="week"> This week</TabsTrigger>
          <TabsTrigger value="month"> This month </TabsTrigger>
          <TabsTrigger value="year"> This year </TabsTrigger>
        </TabsList>
        <TabsContent value="today"> Make changes to your today </TabsContent>
        <TabsContent value="week"> Change your week. </TabsContent>
        <TabsContent value="month"> month </TabsContent>
        <TabsContent value="year"> year </TabsContent>
      </Tabs>
      <!-- <div class="flex items-center gap-4">
        <div
          v-for="(item, index) in 3"
          :key="index"
          class="bg-neutral-200 h-12 w-[120px]"
        ></div>
      </div>
      <section>
        <div class="bg-neutral-200 h-[360px]"></div>
      </section> -->
    </main>
    <footer>
      <div class="grid md:grid-cols-3 grid-cols-1 gap-4">
        <div
          v-for="(item, index) in 3"
          :key="index"
          class="col-span-1 bg-neutral-200 h-[300px]"
        ></div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";
</script>

<style scoped></style>
