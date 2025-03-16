<template>
        <div class="flex lg:items-center mb-5 flex-col lg:flex-row items-start">
            <div class="flex items-center">
                <img src="/public/logo.png" alt="logo" class="w-11 h-11 lg:w-15 lg:h-15 mr-2 lg:mr-4">
                <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо <hr class=" lg:block"> 
                    <template v-if="route.name=== 'index'">Послуги</template> 
                    <template v-if="route.name=== 'board'">Оголошення </template> 
                </h1>
            </div>

            <ul class="flex gap-4 text-2xl my-4 md:mx-10 text-blue-700">
                <li :class="[route.name === 'index' ? 'font-bold underline' : '']"><RouterLink to="/">Послуги</RouterLink></li>
                <li  :class="[route.name === 'board' ? 'font-bold underline' : '']"><RouterLink to="/board">Оголошення</RouterLink></li>
            </ul>

            <a v-if="route.name=== 'index'" href="https://docs.google.com/forms/d/e/1FAIpQLScC6JWHsmvn73hG2FwQkdMOpLi840b64vmsm0oC6Xm37PiAGw/viewform?usp=header" class="w-full lg:w-fit"  target="_blank"> <button class="lg:ml-10 mt-4 lg:mt-0  bg-[#0057b8] w-full lg:w-fit hover:bg-blue-500 px-4 py-2 lg:py-3 text-white uppercase font-bold rounded-3xl cursor-pointer ">Додати послугу</button></a>
        </div>
</template>

<script setup>
import { useRoute } from 'vue-router'


const route = useRoute()




</script>