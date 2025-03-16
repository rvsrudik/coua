<template>
    <div class="border-sky-200 border-1 rounded-xl w-full relative overflow-hidden">
        <!-- <div class="flex gap-2 flex-wrap"> -->
            <!-- <h4 class="bg-zinc-100 whitespace-nowrap px-3 py-1 rounded-lg" v-for="(category, i) in  service.categories"> {{ category }} </h4> -->
        <!-- </div> -->

        <div class="flex">
            <div class="bg-sky-200 shrink-0  w-fit px-3 py-1 text-sm flex items-center  text-gray-800 ">Субота, 28 Лютого 2024, 9:18am</div>
            <h3 class="font-bold py-1 px-3 text-lg bg-sky-100  w-full">USCRI Українська зустріч</h3>
        </div>


        <div class="p-4">
            USCRI має задоволення представити Арслана Аннаоразова, який буде вести дві онлайн групи для спілкування українців російською мовою про життя у США, родину та друзів на батьківщині, а також про життя в умовах невизначеності.
                Зареєструватися тут: https://tinyurl.com/3nk8uw32
                Приєднуйтесь тут: https://tinyurl.com/ms4f899b
        </div>

        <div class="p-4">
            <button class="border-blue-600 border-1 hover:bg-blue-500 px-4 py-2  text-blue-600 uppercase font-bold rounded-3xl cursor-pointer text-sm ">Зареєструватись</button>
            <button class="border-blue-600 border-1 hover:bg-blue-500 px-4 py-2  text-blue-600 uppercase font-bold rounded-3xl cursor-pointer text-sm ml-3">Підʼєднатись</button>
        </div>
        
        
        
        
        <!-- <p v-if="service.phones.length" class="flex gap-1 mb-3">
            <a v-for="(phone, i) in service.phones" :key="i" :href='`tel:${phone}`'>{{phone}}</a> 
        </p> -->
    
        <p v-if="event?.description">{{ event?.description }}</p>
    </div>
</template>
    
<script setup>
    
const props = defineProps({
    event: {}
})
</script>