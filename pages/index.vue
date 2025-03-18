<template>
    <div class="p-4 md:p-6">
        <MainHeader />

        <h2 class="text-2xl font-bold mb-3">Послуги</h2>


        <input v-model="search" class="h-12 rounded-xl mb-4 px-3 w-full sm:w-96  border-1 border-sky-200"  placeholder="Пошук..." type="text">

        <div v-if="loading.categories">Loading categories...</div>
         <div v-else class="flex gap-2 flex-wrap mb-8">
          
            <span v-for="category in categories" :key="category" class="py-1 px-2 rounded-xl cursor-pointer" :class="[selectedCetegory === category.slug ? 'bg-indigo-500 text-gray-200' : 'bg-indigo-100 text-gray-700']" @click="selectedCetegory = selectedCetegory === category.slug ?  null : category.slug">{{ category.icon }} {{ category.name[language] }} </span>
            <span v-if="selectedCetegory" class="py-1 px-2 rounded-xl cursor-pointer border-1 border-indigo-900" @click="selectedCetegory = null">Очистити фільтр</span>
         </div>

         <div v-if="loading.services">Loading services...</div>
         <div class="services-list flex-grow">
              <ServiceCard v-for="(service) in searchServices" :key="service._id" :service="service" :categoriesMap="categoriesMap" />
        </div>

 
    </div>
</template>

<script setup>
import ServiceCard from '~/components/ServiceCard.vue';
import MainHeader from '~/components/MainHeader.vue';


const search = ref('')
const selectedTags = ref([])
const selectedCetegory = ref(null)
const categories = ref(null);
const services = ref(null);
const language = 'uk';
const loading = ref({
    categories: false,
    services: false,
})

const shuffle = (array) => { 
  for (let i = array.length - 1; i > 0; i--) { 
    const j = Math.floor(Math.random() * (i + 1)); 
    [array[i], array[j]] = [array[j], array[i]]; 
  } 
  return array; 
}; 


async function fetchServices() {
    loading.value.services = true;
    const url = "https://www.api-uaco.xyz/services";

    try {
        const response = await fetch(url);
        if (!response.ok) {
        throw new Error(`Response status: ${response.status}`);
        }

        services.value = await response.json();
        // const sorte
        // unsortedCategories.sort((a, b) => a.name.uk.localeCompare(b.name.uk, 'uk', { sensitivity: 'base' }))

        // categories.value = unsortedCategories;
  } catch (error) {
    console.error(error.message);
  } finally {
    loading.value.services = false;
  }
}


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

        categories.value = unsortedCategories;
  } catch (error) {
    console.error(error.message);
  } finally {
    loading.value.categories = false;
  }
}

const categoriesMap = computed(() => {
  const catMap = {}
  
  categories.value?.forEach(c => {
    catMap[c.slug] = c.name[language]
  })

  return catMap
})

const searchServices = computed(() => {
  if (!services.value) {
    return []
  }
  
  const activeAndFiltered = services.value.filter((s) => {
    return s.activeStatus === 'active' && (selectedCetegory.value ? s.category === selectedCetegory.value : true)
    })


  const searchFiltered = activeAndFiltered.filter((s) => {
    const searchString = (s.name + s.address + s.phones.map(({number}) => number).join('') + s.tags.join('') + s.description + categoriesMap.value[s.category]).toLowerCase()
    return searchString.toLowerCase().includes(search.value.toLowerCase())
  })

  console.log(searchFiltered)

    return searchFiltered
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
    fetchServices()
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