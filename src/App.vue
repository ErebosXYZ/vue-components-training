<script setup>
import IdCard from './components/IdCard.vue';
import Random from './components/Random.vue';
import BoxColor from './components/BoxColor.vue';
import CreditCard from './components/CreditCard.vue';
import LikeButton from './components/LikeButton.vue';
import ClickablePicture from './components/ClickablePicture.vue';
import Rating from './components/Rating.vue';
import Dice from './components/Dice.vue';
import Carousel from './components/Carousel.vue';
import DriverCard from './components/DriverCard.vue';

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

<h2>3: Color boxes</h2>
   <BoxColor :r="243" :g="0" :b="52" style="color: white" />
    <BoxColor :r="143" :g="255" :b="58" style="color: black" />

<h2>4: Credit cards</h2>
<div class="card-container">
<CreditCard
      type="Visa"
      number="0123456789018845"
      :expiration-month="3"
      :expiration-year="2021"
      bank="BNP"
      owner="Maxence Bouret"
      bg-color="#11aa99"
      color="white"
    />

    <CreditCard
      type="Master Card"
      number="0123456789010995"
      :expiration-month="3"
      :expiration-year="2021"
      bank="N26"
      owner="Maxence Bouret"
      bg-color="#eeeeee"
      color="#222222"
    />

    <CreditCard
      type="Visa"
      number="0123456789016984"
      :expiration-month="12"
      :expiration-year="2019"
      bank="Name of the Bank"
      owner="Firstname Lastname"
      bg-color="#ddbb55"
      color="white"
    />

    
</div>
<h2>5: Rating</h2>
<Rating :rate="0" />
    <Rating :rate="1.49" />
    <Rating :rate="1.5" />
    <Rating :rate="3" />
    <Rating :rate="4" />
    <Rating :rate="5" />
  
<h2>6: Driver Card</h2>
<div>
    <DriverCard
      name="Travis Kalanick"
      :rating="4.2"
      img="https://si.wsj.net/public/resources/images/BN-TY647_37gql_OR_20170621052140.jpg?width=620&height=428"
      :car="{ model: 'Toyota Corolla Altis', licensePlate: 'CO42DE' }"
    />

    <DriverCard
      name="Dara Khosrowshahi"
      :rating="4.9"
      img="https://ubernewsroomapi.10upcdn.com/wp-content/uploads/2017/09/Dara_ELT_Newsroom_1000px.jpg"
      :car="{ model: 'Audi A3', licensePlate: 'BE33ER' }"
    />
</div>
  
<h2>7: Like Button</h2>
<LikeButton />

<h2>8: Clickable Picture</h2>

<ClickablePicture img="maxence.png" img-clicked="maxence-glasses.png"/>

<h2>9: Dice</h2>
<Dice />

<h2>10: Carousel</h2>
<Carousel 
:images='[
    "https://randomuser.me/api/portraits/women/1.jpg",
    "https://randomuser.me/api/portraits/men/1.jpg",
    "https://randomuser.me/api/portraits/women/2.jpg",
    "https://randomuser.me/api/portraits/men/2.jpg",
  ]'
/>

</template>

<style scoped>
.card-container{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px;
}

</style>
