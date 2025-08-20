<script setup>

import { ref } from 'vue';

const likes = ref(0)
const currentColor = ref('purple')
const colorIndex = ref(0)

const colors = ['purple','blue','green','yellow','orange','red']

const increaseLikes = () => {
    likes.value++
    bgColorChange()
}

const bgColorChange = () => {
    colorIndex.value++
    if (colorIndex.value >= colors.length){
        colorIndex.value = 0
    }
    currentColor.value = colors[colorIndex.value]
}


</script>


<template>
<button :style="{backgroundColor: currentColor, color: 'white'}" class="like__button" @click="increaseLikes">{{ likes }} {{ likes === 1 ? 'Like' : 'Likes' }}</button>
</template>


<style scoped>
.like__button {
    width: 100px;
    height: 40px;
    border-radius: 5px;
    cursor: pointer;
}
</style>