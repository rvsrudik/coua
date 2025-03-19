<template>
    <div class="h-14 bg-white fixed bottom-0 left-0 border-t-1 border-gray-100 shadow-2xl  w-full flex justify-center items-center">
        <ul class="flex gap-8 text-2xl my-4 md:mx-10 text-blue-700">
                <li :class="[route.name === 'index' ? 'font-bold underline' : '']"><RouterLink to="/">Послуги</RouterLink></li>
                <li  :class="[route.name === 'board' ? 'font-bold underline' : '']"><RouterLink to="/board">Оголошення</RouterLink></li>
            </ul>
    </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
const route = useRoute()

</script>