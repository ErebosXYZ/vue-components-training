<template>
    <div class="section">
        <SingleColorPicker color="r" v-model="rValue" />
        <SingleColorPicker color="g" v-model="gValue" />
        <SingleColorPicker color="b" v-model="bValue" />
        <div class="container">
            <div class="square" :style="{ backgroundColor: bgColor }"></div>
            <p class="rgb-text">rgb({{ rValue }}, {{ gValue }}, {{ bValue }})</p>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import SingleColorPicker from './SingleColorPicker.vue'

const rValue = ref(0)
const gValue = ref(0)
const bValue = ref(0)

const bgColor = computed(() => {
    return `rgb(${rValue.value}, ${gValue.value}, ${bValue.value})`
})
</script>

<style scoped>
.section {
    margin: 8px;
}

.container {
    display: flex;
    flex-direction: row;
    gap: 5px;
    align-items: center;
    margin: 5px;
}

.square {
    border: solid black;
    height: 5vw;
    width: 5vw;
}
</style>