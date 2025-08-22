<template>
  <div class="container">
    <div
      class="square"
      :style="{ backgroundColor: squareColor }"
    ></div>
    <span class="color">{{ color.toUpperCase() }}:</span>
    <input
      type="number"
      min="0"
      max="255"
      :value="value"
      @input="onInput"
    />
    
  </div>
</template>

<script setup>
import { computed } from 'vue'

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

const emit = defineEmits(['change'])

const squareColor = computed(() => {
  if (props.color === 'r') return `rgb(${props.value},0,0)`
  if (props.color === 'g') return `rgb(0,${props.value},0)`
  if (props.color === 'b') return `rgb(0,0,${props.value})`
  return 'black'
})

function onInput(event) {
  let val = Number(event.target.value)
  if (val < 0) val = 0
  if (val > 255) val = 255
  emit('change', val)
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  gap: 8px;
  align-items: center;
  margin: 5px;
}

.square {
  border: solid 2px black;
  height: 30px;
  width: 30px;
}

.color {
  font-weight: bold;
}
</style>
