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
      <Tabs default-value="account">
        <TabsList class="max-w-[400px]">
          <TabsTrigger
            v-for="(item, index) in tabs"
            :key="index"
            :value="item.title"
            @click="handleTabClick(item.title)"
          >
            {{ item.title }}
          </TabsTrigger>
        </TabsList>
        <TabsContent
          v-for="(item, index) in tabs"
          :key="index"
          :value="item.title"
        >
          <!-- Render the component dynamically -->
          <component :is="item.component" />
        </TabsContent>
        <!-- Highchart component render -->
        <highchart :options="options" />
      </Tabs>
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
import TabsToday from "../../components/Tabs/Today.vue";
import TabsMonth from "../../components/Tabs/Month.vue";
import TabsYear from "../../components/Tabs/Year.vue";
import TabsWeek from "../../components/Tabs/Week.vue";
import { ref, computed, onMounted } from "vue";

const tabs = [
  { title: 'today', component: TabsToday },
  { title: 'week', component: TabsWeek },
  { title: 'month', component: TabsMonth },
  { title: 'year', component: TabsYear },
];

const data = ref(generateRandomData()); // Initial data
const categories = ref({
  today: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
  week: ['Week 1', 'Week 2', 'Week 3', 'Week 4'],
  month: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
  year: ['2020', '2021', '2022', '2023', '2024'],
});

const currentCategory = ref('today');

function generateRandomData(number = 7) {
  return Array.from({ length: number }, () => Math.floor(Math.random() * 100));
}

function handleTabClick(tabTitle) {
  currentCategory.value = tabTitle.toLowerCase();
  data.value = generateRandomData(categories.value[currentCategory.value].length || 7);
}

const options = computed(() => ({
  chart: {
    type: 'line',
    animation: { enabled: false },
  },
  title: {
    text: 'Monthly Average Temperature',
  },
  xAxis: {
    categories: categories.value[currentCategory.value],
    gridLineColor: 'transparent',
  },
  yAxis: {
    title: { text: 'Temperature (°C)' },
    gridLineColor: 'transparent',
  },
  plotOptions: {
    line: {
      marker: { enabled: false },
      dataLabels: { enabled: true },
      enableMouseTracking: true,
    },
  },
  series: [
    {
      name: 'Reggane',
      lineWidth: 4,
      color: {
        linearGradient: { x1: 0, y1: 0, x2: 1, y2: 0 },
        stops: [
          [0, 'red'],
          [0.25, 'blue'],
          [1, 'green'],
        ],
      },
      data: data.value,
    },
  ],
}));

onMounted(() => {
  data.value = generateRandomData(); // Generate initial data on mount
});
</script>

<style scoped></style>
