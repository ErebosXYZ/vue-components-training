<script setup>
import IdCard from './components/IdCard.vue';
import Random from './components/Random.vue';
</script>

<template>
  <h1>Creación de componentes con Vue</h1>
  <p>Crea a conitnuación todos los componentes del ejercicio.</p>
  <h2>1: IdCard</h2>
  <IdCard first-name="John" last-name="Doe" gender="male" :height="178" :birth='new Date("1992-07-14")' picture="https://xsgames.co/randomusers/avatar.php?g=male"/>
  <IdCard
  last-name='Delores '
  first-name='Obrien'
  gender='female'
  :height="172"
  :birth='new Date("1988-05-11")'
  picture="https://xsgames.co/randomusers/avatar.php?g=female"
/>
<h2>2: Random integers</h2>
<Random :min="1" :max="6"/>
<Random :min="1" :max="100"/>
</template>

<style scoped>

</style>
