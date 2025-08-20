<script setup>
import { computed } from 'vue';

const props = defineProps({
    rate: Number
})

const fillStars = computed(() => {
    return Math.round(props.rate)
})

const emptyStars = computed(() => {
    return 5 - fillStars.value
})
</script>

<template>
   <div class="stars">
    <span v-for="r in fillStars">★</span>
    <span v-for="r in emptyStars">☆</span>
   </div>
</template>

<style scoped>
    .stars {
        font-size: xx-large;
    }

</style>