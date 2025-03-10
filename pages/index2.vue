<template>
    <div class="p-4 md:p-6">
        <div class="flex lg:items-center mb-5 flex-col lg:flex-row items-start">
            <div class="flex items-center">
                <img src="/public/logo.png" alt="logo" class="w-11 h-11 lg:w-15 lg:h-15 mr-2 lg:mr-4">
                <h1 class="uppercase font-bold lg:text-2xl ">Українці в Колорадо <hr class=" lg:block"> Послуги</h1>
            </div>

            <a href="https://docs.google.com/forms/d/e/1FAIpQLScC6JWHsmvn73hG2FwQkdMOpLi840b64vmsm0oC6Xm37PiAGw/viewform?usp=header" class="w-full lg:w-fit"  target="_blank"> <button class="lg:ml-10 mt-4 lg:mt-0  bg-[#0057b8] w-full lg:w-fit hover:bg-blue-500 px-4 py-2 lg:py-3 text-white uppercase font-bold rounded-3xl cursor-pointer ">Додати послугу</button></a>
        </div>


        <input v-model="search" class="h-12 rounded-xl mb-4 px-3 w-full sm:w-96  border-1 border-sky-200"  placeholder="Пошук..." type="text">

        <div v-if="loading.categories">Loading...</div>
         <div v-else class="flex gap-2 flex-wrap mb-8">
            <span v-for="tag in categories" :key="tag" class="py-1 px-2 rounded-xl cursor-pointer" :class="[selectedTag === tag.slug ? 'bg-indigo-500 text-gray-200' : 'bg-indigo-100 text-gray-700']" @click="selectedTag = tag.slug">{{ tag.name[language] }} </span>
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
const selectedTag = ref(null)
const categories = ref(null);
const language = 'uk';
const loading = ref({
    categories: false
})

async function fetchCategories() {
    loading.value.categories = true;
    const url = "https://www.api-uaco.xyz/services/categories";

    try {
        const response = await fetch(url);
        if (!response.ok) {
        throw new Error(`Response status: ${response.status}`);
        }

        const unsortedCategories = await response.json();
        unsortedCategories.sort((a, b) => a.name.uk.localeCompare(b.name.uk, 'uk', { sensitivity: 'base' }))

        console.log('a', unsortedCategories)

        categories.value = unsortedCategories;
  } catch (error) {
    console.error(error.message);
  } finally {
    loading.value.categories = false;
  }
}

const searchServices = computed(() => {
    return services.filter((s) => {
        const searchString = (s.name + s.address + s.phones.join('') + s.categories.join('') + s.description).toLowerCase()
        return searchString.toLowerCase().includes(search.value.toLowerCase()) && (selectedTags.value.length ? s.categories.find(c => selectedTags.value.includes(c)) : true)
    })
})


function onClickTag(tag) {
    if (selectedTags.value.includes(tag)) {
        selectedTags.value = selectedTags.value.filter(t => t !== tag)
    } else {
        selectedTags.value.push(tag)
    }
}

onMounted(() => {
    fetchCategories()
})

useHead({
  title: 'Українці в Колорадо | Послуги',
  meta: [
    { name: 'description', content: 'Платформа для українців у Колорадо, яка дозволяє знаходити та додавати послуги й сервіси в різних сферах, таких як ремонт, освіта, медицина, доставка, юридична допомога, ІТ-послуги та багато іншого.' }
  ]
})

</script>

<style scoped>
    .services-list {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
    }
</style>