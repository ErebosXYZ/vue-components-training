<script setup>
import { computed } from 'vue'
const props = defineProps({
    limit: Number
})

const numbers = computed(() => {

    const numbersArray = []
    for (let i = 1; i <= props.limit; i++) {
        numbersArray.push({
            value: i,
            backgroundColor: i % 2 === 0 ? "red" : "white"
        })
    }
    return numbersArray
})
</script>

<template>
    <div class="container">
        <span v-for="n in numbers" :key="n.value" :style="{ backgroundColor: n.backgroundColor}">{{ n.value }}</span>
    </div>
</template>


<style scoped>

.container {
    margin: 5rem;
    display: flex;
    flex-wrap: wrap;
    
}

span {
    border: solid black;
    color: black;
    width: 2rem;
    height: 2rem;
    padding: 2rem;
    justify-content: center;
    align-items: center;
}

</style>