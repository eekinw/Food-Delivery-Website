<script setup>
import {ref, computed} from "vue"

import valuesData from "../values.json"

const values = ref(valuesData);
const displayedCards = ref(4);
const showOrHide = ref("Show All Values")

const filteredValues = computed(() => values.value.slice(0, displayedCards.value))

const toggleCards = () => {
    if(displayedCards.value === values.value.length) {
        displayedCards.value = 4;
        showOrHide.value = "Show All Values";
    } else {
        displayedCards.value = values.value.length;
        showOrHide.value = "Hide All Values"
    }
}

</script>

<template>

    <div class="h-auto w-full bg-slate-300 p-10 flex flex-col">
        <h1 class=" text-center text-4xl font-bold mb-10">Our Values</h1>
    
        <div class="grid grid-cols-4 gap-5 place-content-evenly text-left">
            <div class="bg-white rounded-lg p-3"
            v-for="(card, index) in filteredValues"
            :key="card.id"
            >
            <h2 class="text-lg font-bold">{{ card.title}}</h2>
            <p>{{ card.content }}</p>
            </div>
        </div>

        <div class="flex justify-center">
            <button class="mt-10 border-solid border-2 border-white w-1/5 p-2 rounded-lg" @click="toggleCards">{{ showOrHide}}</button>
        </div>
    </div>

</template>

