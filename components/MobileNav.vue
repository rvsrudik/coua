<template>
    <div class="h-14 bg-white fixed bottom-0 left-0 border-t-1 border-gray-100 shadow-2xl w-full flex justify-center items-center">
        <ul class="text-lg h-full flex-nowrap md:mx-10 text-gray-700 flex w-full" :class="`grid-cols-${mainNav.length}`">
            <RouterLink  v-for="(menuItem, i) in mainNav" :key="i" :to="{name: menuItem.routeName}" class="w-full"><li  :class="[route.name === menuItem.routeName ? 'bg-gray-200 font-bold' : '']" class="h-full flex items-center justify-center">{{ menuItem.title }}</li></RouterLink>
        </ul>
    </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { mainNav } from '~/data/menu.js'
const route = useRoute()

</script>