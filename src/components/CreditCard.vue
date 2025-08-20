<script setup>
import { computed } from "vue"
import visaLogo from "../assets/images/visa.png"
import masterCardLogo from "../assets/images/master-card.svg"

const props = defineProps({
    type: {
        type: String,
        validator (value, props){
            return ['Visa', 'Master Card'].includes(value)
        }
    },
    number: String,
    expirationMonth: {
        type: Number,
        validator: (val) => val >= 1 && val <= 12
    },
    expirationYear: Number,
    bank: String,
    owner: String,
    bgColor: String,
    color: String
})

const cardImage = computed(() => {
  const images = {
    Visa: visaLogo,
    "Master Card": masterCardLogo,
  };
  return images[props.type] || "";
});

const formattedCardNumber = computed(() => {
    if (!props.number){
        return ""
    }
  const cleanNumber = props.number.replace(/\D/g, "");
    const groups = cleanNumber.match(/.{1,4}/g) || [];
    return groups.map((group, index) => { 
        if (index < 3 && group.length === 4) {
            return "****";
        }
        return group
    }).join(" ");
})
</script>

<template>
    <div class="card" :style="{ backgroundColor: bgColor, color: color}">
        <img :src="cardImage" :alt="props.type">
        <div class="card-number">{{ formattedCardNumber }}</div>
        <div class="card-bottom">
            <p>Expires {{ expirationMonth }}/{{ expirationYear }}</p>
            <p>{{ bank }}</p>
            <p>{{ owner }}</p>
        </div>
    </div>
</template>

<style scoped>
.card {
     display: inline-flex;
    flex-direction: column;
    padding: 1rem;
    border-radius: 8px;
    gap: 0.6em;
    line-height: 1em;
}
.card img {
     width: 50px;
    align-self: flex-end;
}
.card-number {
     font-weight: bold;
    font-size: 1.2rem;
    align-self: center;
    
}
.card-bottom {
       margin-left: 1em;

}

</style>