<script setup>
import {useRoute, useRouter} from "vue-router"
import restaurantData from "../restaurant.json"
import {ref, computed, watch} from "vue"
const restaurants = ref(restaurantData)

const route = useRoute();
const router = useRouter();

const filteredRestaurants = computed(() => {
    const cuisine = route.params.cuisine.toLowerCase()
    return restaurants.value.filter((restaurant) => restaurant.cuisine.toLowerCase() === cuisine)
}
)

// filter restaurants by price

const restaurantPrice = ref("")


// add a watch to filter the prices based on the select and v-model

watch(restaurantPrice, () => {
  if(restaurantPrice.value) {
    if(restaurantPrice.value === "All") restaurants.value = restaurantData;
    else {
      restaurants.value = restaurantData.filter(r => r.price === restaurantPrice.value);
    }
  } 
})

</script>

<template>
  <main class="h-60 w-full flex justify-center items-center flex-wrap">
        <div
          class="shadow-md p-4 w-30 mr-4 cursor-pointer mb-4 text-center"
          v-for="restaurant in filteredRestaurants"
          :key="restaurant.id"
        >
          <h1 class="text-2xl bold mb-3">{{ restaurant.name }}</h1>
          <p class="italic">{{ restaurant.cuisine }}</p>
          <p class=" text-yellow-200">{{ restaurant.price }}</p>
        </div>
        <button class="border-solid border-2 border-sky-500 p-2 rounded-lg" @click="router.back()">Go Back</button>
        <select class="ml-5 rounded-md w-auto" v-model="restaurantPrice">
          <option value="All">All</option>
          <option value="$">$</option>
          <option value="$$">$$</option>
          <option value="$$$">$$$</option>
        </select>
    </main>

</template>
