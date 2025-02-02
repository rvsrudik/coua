<template>
<div class="p-4 border-sky-200 border-1 rounded-xl w-full sm:w-fit sm:max-w-[280px]">
    <div class="flex gap-2 flex-wrap">
        <h4 class="bg-zinc-100 whitespace-nowrap px-3 py-1 rounded-lg" v-for="(category, i) in  service.categories"> {{ category }} </h4>
    </div>
    
    <h3 class="font-bold my-3">{{ service.name  }}</h3>
    <p v-if="service.phones.length" class="flex gap-1 mb-3">
        <a v-for="(phone, i) in service.phones" :key="i" :href='`tel:${phone}`'>{{phone}}</a> 
    </p>

    <p v-if="service.description">{{  service.description  }}</p>
</div>
</template>

<script setup>

const props = defineProps({
    service: {}
})
</script>