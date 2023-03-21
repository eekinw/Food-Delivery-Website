<script setup>
import {RouterView, RouterLink, useRouter} from "vue-router"
import {ref} from "vue"
import restaurantData from "../restaurant.json"
import Nav from "../components/Nav.vue"
import Hero from "../components/Hero.vue"
import ScrollingCard from "../components/ScrollingCard.vue"
import MapCard from "../components/MapCard.vue"
import Banner from "../components/Banner.vue"
import RestaurantView from "../views/RestaurantView.vue"
import Footer from "../components/Footer.vue"

const router = useRouter()

const restaurants = ref(restaurantData)

</script>

<template>
  <Nav />

  <Hero />
  
<ScrollingCard />

<!-- Map Card-->
<MapCard />

<!-- Banner Hot Deals -->
<Banner />


<!-- Type of Cuisine -->
<div class="w-full grid grid-rows-4 md:grid-rows-2 grid-flow-col gap-3 md:gap-x-2 place-items-center mb-5">
  <div class="relative w-auto mr-4 cursor-pointer mb-4 text-center hover:scale-110" @click="router.push({ path: '/restaurants/japanese' })">
      <img class="object-cover h-48 w-96 md:h-96 md:w-192 lg-w-384 rounded-lg" src="../assets/japanese.jpg" alt="">
      <p class="absolute top-1/3 text-2xl lg:text-3xl text-slate-100 w-full text- italic">Japanese</p>
  </div>
  <div class="relative w-auto mr-4 cursor-pointer mb-4 text-center hover:scale-110" @click="router.push({ path: '/restaurants/chinese' })">
    <img class="object-cover h-48 w-96 md:h-96 md:w-192 lg:w-384 rounded-lg" src="../assets/chinese.jpg" alt="">
    <p class="absolute top-1/3 text-2xl lg:text-3xl text-slate-100 w-full text- italic">Chinese</p>
  </div>
  <div class="relative w-auto mr-4 cursor-pointer mb-4 text-center hover:scale-110" @click="router.push({ path: '/restaurants/indian' })">
    <img class="object-cover h-48 w-96 md:h-96 md:w-192 lg:w-384 rounded-lg" src="../assets/indian.jpg" alt="">
    <p class="absolute top-1/3 text-2xl lg:text-3xl text-slate-100 w-full text- italic">Indian</p>
  </div>
  <div class="relative w-auto mr-4 cursor-pointer mb-4 text-center hover:scale-110" @click="router.push({ path: '/restaurants/korean' })">
    <img class="object-cover h-48 w-96 md:h-96 md:w-192 lg:w-384 rounded-lg" src="../assets/korean.jpg" alt="">
    <p class="absolute top-1/3 text-2xl lg:text-3xl text-slate-100 w-full text- italic">Korean</p>

  </div>
</div>


<!-- Help & Footer Section -->
<Footer />



</template>

