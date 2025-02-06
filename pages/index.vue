<template>
    <div class="p-4 md:p-6">
        <div class="flex lg:items-center mb-5 flex-col lg:flex-row items-start">
            <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо | Послуги</h1>

            <a href="https://docs.google.com/forms/d/e/1FAIpQLScC6JWHsmvn73hG2FwQkdMOpLi840b64vmsm0oC6Xm37PiAGw/viewform?usp=header" target="_blank"> <button class="lg:ml-6 mt-3 lg:mt-0 bg-blue-600 hover:bg-blue-500 px-4 py-2 lg:py-3 text-white uppercase font-bold rounded-3xl cursor-pointer ">Додати послугу</button></a>
        </div>


        <input v-model="search" class="h-12 rounded-xl mb-4 px-3 w-full sm:w-96  border-1 border-sky-200"  placeholder="Пошук..." type="text">

        <!-- filters -->
         <div  class="flex gap-2 flex-wrap mb-8">
            <span v-for="tag in categories" :key="tag" class="py-1 px-2 rounded-xl cursor-pointer" :class="[selectedTags.includes(tag) ? 'bg-indigo-500 text-gray-200' : 'bg-indigo-100 text-gray-700']" @click="onClickTag(tag)">{{ tag }} <span v-if="selectedTags.includes(tag)" class="font-bold ml-1 text-gray-800">x</span> </span>
            <span v-if="selectedTags.length" class="py-1 px-2 rounded-xl cursor-pointer border-1 border-indigo-900" @click="selectedTags = []">Очистити фільтр</span>

         </div>

        <div class="services-list">
            <ServiceCard v-for="(service, i) in searchServices" :key="i" :service="service" />
        </div>
    </div>
</template>

<script setup>
import services from '~/content/services';
import ServiceCard from '~/components/ServiceCard.vue';

const search = ref('')
const selectedTags = ref([])

const searchServices = computed(() => {
    return services.filter((s) => {
        const searchString = (s.name + s.address + s.phones.join('') + s.categories.join('') + s.description).toLowerCase()
        return searchString.toLowerCase().includes(search.value.toLowerCase()) && (selectedTags.value.length ? s.categories.find(c => selectedTags.value.includes(c)) : true)
    })
})

const categories = computed(() => {
    return [...new Set(services.map(s => s.categories[0]))]
})

function onClickTag(tag) {
    if (selectedTags.value.includes(tag)) {
        selectedTags.value = selectedTags.value.filter(t => t !== tag)
    } else {
        selectedTags.value.push(tag)
    }
}
</script>

<style scoped>
    .services-list {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
    }
</style>