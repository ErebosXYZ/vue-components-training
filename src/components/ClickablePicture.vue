<script setup>
import { ref } from 'vue';
const props = defineProps({
    img: String,
    imgClicked: String
})

const currentImage = ref(props.img)

const toggleImage = () => {
   currentImage.value = currentImage.value === props.img ? props.imgClicked : props.img
}

</script>


<template>
<img class="clickable__picture" @click="toggleImage" :src="currentImage" alt="Clickable Picture">
</template>


<style scoped>
.clickable__picture {
    cursor: pointer;

}
</style>