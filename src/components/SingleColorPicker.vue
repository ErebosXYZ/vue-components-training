<template>
    <div class="container">
        <div class="square" :style="{ backgroundColor: bgColor }"></div>
        <label :for="color" class="color">{{ color.toUpperCase() }}:</label>
        <input 
            type="number" 
            :id="color" 
            v-model.number="localValue" 
            min="0" 
            max="255"
            @input="emitChange"
        >
    </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'

const props = defineProps({
    color: {
        type: String,
        validator: (val) => ['r', 'g', 'b'].includes(val),
        required: true
    },
    value: {
        type: Number,
        validator: (val) => val >= 0 && val <= 255,
        required: true
    }
})

const emit = defineEmits(['update:value'])

const localValue = ref(props.value)

// Sync localValue with props.value when it changes
watch(() => props.value, (newValue) => {
    localValue.value = newValue
})

// Emit changes when localValue changes
const emitChange = () => {
    emit('update:value', localValue.value)
}

const bgColor = computed(() => {
    return `rgb(${
        props.color === 'r' ? localValue.value : 0
    },${
        props.color === 'g' ? localValue.value : 0
    },${
        props.color === 'b' ? localValue.value : 0
    })`
})
</script>

<style scoped>
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

.color {
    text-transform: uppercase;
}
</style>