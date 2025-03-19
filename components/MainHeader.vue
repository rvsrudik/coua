<template>
        <div class="flex lg:items-center mb-5 flex-col lg:flex-row items-start">
            <div class="flex items-center">
                <img src="/public/logo.png" alt="logo" class="w-11 h-11 lg:w-15 lg:h-15 mr-2 lg:mr-4">
                <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо <hr class=" lg:block"> 
                    <template v-if="route.name=== 'index'">Послуги</template> 
                    <template v-if="route.name=== 'board'">Оголошення </template> 
                </h1>
            </div>

            <ul class="gap-4 text-2xl my-4 md:mx-10 text-blue-700 hidden sm:flex">
                <li :class="[route.name === 'index' ? 'font-bold underline' : '']"><RouterLink to="/">Послуги</RouterLink></li>
                <li  :class="[route.name === 'board' ? 'font-bold underline' : '']"><RouterLink to="/board">Оголошення</RouterLink></li>
            </ul>
        </div>
</template>

<script setup>
import { useRoute } from 'vue-router'


const route = useRoute()




</script>