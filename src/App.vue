<script setup lang="ts">
import Video from './components/Video.vue';
import data from "./assets/data.json";
import Players from "./components/Players.vue"
import { ref, watch } from 'vue';

interface Year {
  id: string,
  link: string
}

const years = data.years;
const selected = ref<Year>({"id": "2022", "link": "https://www.youtube.com/embed/Q2VfUqpLYLo?si=ZnaOwZkHS2xXYzRh"});

watch(selected, (newSelected) => {
  console.log(newSelected)
});
</script>

<template>
  <div class="drawer drawer-open overflow-hidden">
    <input id="my-drawer" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content object-scale-down">
      <div class="navbar w-full shadow-md sticky top-0 z-30 bg-base-100 flex justify-between">
        <h2 class="text-3xl text-accent font-bold">Year: {{ selected?.id }}</h2>
        <select v-model="selected" class="select select-sm select-accent">
            <option v-for="year in years" :key="year.id" :value="year">
                {{ year.id }}
            </option>
        </select>
      </div>
      <Video :year="selected"/>
    </div>
    <div class="drawer-side z-40">
      <aside class="w-80 h-screen">
        <header class="bg-base-100 flex sticky top-0 z-20 items-center justify-center shadow-md px-4 px-2 h-16">
          <h1 class="text-5xl text-accent font-bold">Billboards</h1>
        </header>
        <div class="h-4"></div>
        <Players/>
      </aside>
    </div>
  </div>
</template>
