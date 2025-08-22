<script setup>
import { ref } from 'vue';
import Rating from './Rating.vue';

const props = defineProps({
    name: String,
    rating: {
        type: Number,
        validator: (val) => val >= 0 && val <= 5
    },
    img: String,
    car: {
        type: Object,
        default: () => ({ model: '', licensePlate: ''})
    }
})

const picture = ref(props.img)
</script>


<template>

<div class="container">
<img :src="picture" alt="">
<div class="car__data">
<h3>{{ name }}</h3>
<Rating :rate="rating"/>
<p>{{ car.model }} - {{ car.licensePlate }}</p>
</div>


</div>

</template>


<style scoped>
.container {
    background-color: rgba(38, 120, 252, 0.773);
    border-radius: 10px;
    margin: 10px;
    padding: 20px;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    gap: 2px;
    
}
.car__data {
    margin-left: 2vw;
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: start;
}
img {
    width: 10vw;
    height: 10vw;
    border-radius: 100px;
}

</style>