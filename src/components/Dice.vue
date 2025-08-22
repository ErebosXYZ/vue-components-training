<script setup>
import { ref, computed } from 'vue';
import emptyDice from '../assets/images/dice-empty.png'
import dice1 from '../assets/images/dice1.png'
import dice2 from '../assets/images/dice2.png'
import dice3 from '../assets/images/dice3.png'
import dice4 from '../assets/images/dice4.png'
import dice5 from '../assets/images/dice5.png'
import dice6 from '../assets/images/dice6.png'

const dice = ref(emptyDice)

const possibleRolls = [dice1, dice2, dice3, dice4, dice5, dice6]

const diceRoll = () => {
    setTimeout(() => {
        const randomIndex = Math.floor(Math.random() * possibleRolls.length)
        dice.value = possibleRolls[randomIndex]
    }, 1000)

}
</script>

<template>
    <img @click="diceRoll" class="dice" :src="dice" alt="Roll the dice!">
</template>


<style scoped>
.dice {
    width: 30vw;
    height: auto;
}
</style>