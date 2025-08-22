<template>
    <div class="section">
        <div class="countries"> <button v-for="c in countries" :key="c" class="countries__button" :class="{ 'countries__button--active': selectedCountry === c }" @click="selectedCountry = c">{{ c }}</button>
        </div>
        <div class="container" v-for="p in profiles" :class="{ 'highlighted': selectedCountry && p.country === selectedCountry}">
            <img  :src="p.img" alt="Profile picture">
            <div class="student-data">
                <p><span>First name: </span>{{ p.firstName }}</p>
                <p><span>Last name: </span>{{ p.lastName }}</p>
                <p><span>Country: </span>{{ p.country }}</p>
                <p><span>Type: </span>{{ p.isStudent ? 'Student' : 'Teacher' }}</p>
            </div>

        </div>
    </div>

</template>

<script setup>
import { ref, computed } from "vue";
import profiles from "../data/berlin.json";
const selectedCountry = ref(null);

const countries = computed(() => {
    return [...new Set(profiles.map(p => p.country))]
})


</script>

<style scoped>
.section {
    display: flex;
    flex-direction: column;
    gap: 2vh;
}

.container {
    border: solid black;
    display: flex;
    flex-direction: row;
    padding: 1vw;
    gap: 2vw;
    color: black;
    max-width: 60vw;
}

.countries {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 1vw;

    .countries__button {
        border-radius: 0%;
        background-color: white;
        border: rgba(147, 147, 147, 0.674) solid 2px;
        box-shadow: 1px 1px rgba(0, 0, 0, 0.267);
        padding: 5px;
    }
    .countries__button:hover {
        background-color: rgba(115, 158, 252, 0.712);
        
    }

    .countries__button--active {
        background-color: rgba(115, 158, 252, 0.712);
        
    }
}

.highlighted {
    background-color: rgba(115, 158, 252, 0.712);
}
span {
    font-weight: bold;
}

img {
    width: 15vw;
    height: auto;
}
</style>