<script setup lang="ts">
import Video from './components/Video.vue';
import data from "./assets/data.json";
import { ref } from 'vue';

interface Year {
  id: string,
  link: string
}

const years = data.years;
const selected = ref<Year>({"id": "2022", "link": "https://www.youtube.com/embed/Q2VfUqpLYLo?si=ZnaOwZkHS2xXYzRh"});

</script>

<template>
  <h1>Year: {{ selected?.id }}</h1>
    <select v-model="selected">
        <option disabled value="">Please select a year</option>
        <option v-for="year in years" :key="year.id" :value="year.link">
            {{ year.id }}
        </option>
    </select>
  <Video :year="selected"/>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
