<script setup>
import { computed } from 'vue';
const props = defineProps({
    lastName: String,
    firstName: String,
    gender: {
        type: String,
        validator (value, props){
            return ['male', 'female', 'non-binary'].includes(value)
        }
    },
    height: Number,
    birth: Date,
    picture: String

})

const formattedBirth = computed(() => {
  if (!(props.birth instanceof Date)) return props.birth
  return props.birth.toDateString()
})


</script>

<template>
   <div class="container">
    <img :src="picture" alt="foto de perfil" />

    <div class="user-data">
    
    <p><strong>First Name:</strong> {{ firstName }}</p>
    <p><strong>Last Name:</strong> {{ lastName }}</p>
    <p><strong>Gender:</strong> {{ gender }}</p>
    <p><strong>Height:</strong> {{ height / 100 }}m</p>
    <p><strong>Birth:</strong> {{ formattedBirth }}</p>
    </div>
    
  </div>
</template>

<style scoped>
.container {
    border: solid black;
    margin: 5px;
    padding: 5px;
    display: grid;
    grid-template-columns: 1fr 3fr;
    gap: 5px;

}

img {
    max-width: 150px;
    height: auto;

}
</style>