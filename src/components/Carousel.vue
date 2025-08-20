<script setup>
import { ref } from 'vue';

defineProps({
    images: Array
})

const index = ref(0)

const leftButton = () => {
    if (index.value > 0){
        index.value--
    } 
    

}

const rightButton = () => {
    if (index.value < 3){
        index.value++
    }
    
}

</script>


<template>
<div>
    <button @click="leftButton">Left</button>
    <img :src="images[index]" alt="">
    <button @click="rightButton">Right</button>
</div>
</template>


<style scoped>

</style>