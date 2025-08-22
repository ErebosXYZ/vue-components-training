<template>
    <div class="section">
        <SingleColorPicker color="r" :value="rValue" @change="updateColor('r', $event)" />
        <SingleColorPicker color="g" :value="gValue" @change="updateColor('g', $event)" />
        <SingleColorPicker color="b" :value="bValue" @change="updateColor('b', $event)" />
        <div class="container">
            <div class="result-square" :style="{ backgroundColor: rgbColor }"></div>
            <p>rgb({{ rValue }},{{ gValue }},{{ bValue }})</p>
        </div>

    </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import SingleColorPicker from './SingleColorPicker.vue'

const rValue = ref(255)
const gValue = ref(255)
const bValue = ref(255)

const rgbColor = computed(() => `rgb(${rValue.value}, ${gValue.value}, ${bValue.value})`)

function updateColor(color, val) {
    if (color === 'r') rValue.value = val
    if (color === 'g') gValue.value = val
    if (color === 'b') bValue.value = val
}
</script>

<style scoped>
.section {
    margin: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.result-square {
    border: solid 2px black;
    height: 30px;
    width: 30px;
    margin-left: 5px;
}

.container {
    display: flex;
    flex-direction: row;
    gap: 8px;
    align-items: center;
}
</style>
