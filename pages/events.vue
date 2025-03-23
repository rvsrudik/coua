<template>

        <!-- <div class="flex lg:items-center mb-5 flex-col lg:flex-row items-start">
            <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо | Eвенти</h1>

            <a href="https://docs.google.com/forms/d/e/1FAIpQLScC6JWHsmvn73hG2FwQkdMOpLi840b64vmsm0oC6Xm37PiAGw/viewform?usp=header" target="_blank"> <button class="lg:ml-6 mt-3 lg:mt-0 bg-blue-600 hover:bg-blue-500 px-4 py-2 lg:py-3 text-white uppercase font-bold rounded-3xl cursor-pointer ">Додати евент</button></a>
        </div> -->


        <input v-model="search" class="h-12 rounded-xl mb-4 px-3 w-full sm:w-96  border-1 border-sky-200"  placeholder="Пошук..." type="text">


        <div class="flex flex-col gap-3">
            <EventCard v-for="i in 10" :key="i" />
        </div>

        <FloatingButton link="https://docs.google.com/forms/d/e/1FAIpQLScC6JWHsmvn73hG2FwQkdMOpLi840b64vmsm0oC6Xm37PiAGw/viewform?usp=header" />
</template>

<script setup>
import EventCard from '~/components/EventCard.vue';

</script>

<style scoped>
</style>