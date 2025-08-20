<script setup>
import { computed } from 'vue'
const props = defineProps({
    r: {
        type: Number,
        validator: (val) => val >= 0 && val <= 255
    },
    g: {
        type: Number,
        validator: (val) => val >= 0 && val <= 255
    },
    b: {
        type: Number,
        validator: (val) => val >= 0 && val <= 255
    }
})

const stringRGB = computed(() => {
    return `rgb(${props.r},${props.g},${props.b})`
})
const rgbToHex = (r, g, b) => {
    const toHex = (val) => {
        const hex = val.toString(16)
        return hex.length === 1 ? "0" + hex : hex
    }

    return `#${toHex(r)}${toHex(g)}${toHex(b)}`
}

const stringHEX = computed(() => rgbToHex(props.r, props.g, props.b))


</script>

<template>
<div class="container" :style="{ backgroundColor: stringRGB }">
    <p>{{ stringRGB }}</p>
     <p>{{ stringHEX }}</p>
</div>
</template>

<style scoped>
    .container {
        border: solid black 2px;
    margin: 10px;
    padding: 25px;
    width: 300px;
    height: 75px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    }
</style>