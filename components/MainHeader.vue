<template>
        <div class="flex mb-5 flex-col lg:flex-row items-start">
            <div class="flex items-center">
                <RouterLink to="/">
                    <img src="/public/logo.png" alt="logo" class="w-11 h-11 lg:w-15 lg:h-15 mr-2 lg:mr-4">
                </RouterLink>
                <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо <hr class=" lg:block"> 
                    {{ titles[route.name] }}
                </h1>
            </div>

            <ul class="gap-4 text-2xl md:mx-10 text-gray-700 hidden sm:flex align-top">
                <li v-for="menuItem in mainNav" :class="[route.name === menuItem.routeName ? 'font-bold' : '']"><RouterLink :to="{name: menuItem.routeName}">{{ menuItem.title }}</RouterLink></li>
            </ul>
        </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { mainNav } from '~/data/menu.js'

const route = useRoute()

const titles = {
    index: 'Послуги',
    board: 'Оголошення',
    events: 'Події'
}




</script>