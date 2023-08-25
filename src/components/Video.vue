<script setup lang="ts">
interface Year {
    id: string,
    link: string
}
const props = defineProps<{
    year: Year
}>()


</script>

<template>
    <iframe
    width="100%" 
    height="100%" 
    v-bind:src="props.year.link"
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen>
    </iframe>
</template>