<script setup>
import { computed } from 'vue'
const props = defineProps({
    min: {
        type: Number,
    },
    max: {
        type: Number,
    } 
})

const randomNumber = (min, max) => {
    return Math.floor(Math.random() * (max - min) + min)
}
</script>

<template>
<p>Random value between {{ min }} and {{ max }} => {{ randomNumber(min, max) }}</p>
</template>

<style scoped>

</style>