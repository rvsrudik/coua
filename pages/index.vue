<template>
    <div class="p-4 md:p-6">
        <h1 class="uppercase font-bold text-2xl mb-5">Українці в Колорадо | Послуги</h1>

        <input v-model="search" class="h-12 rounded-xl mb-4 px-3 w-full sm:w-96  border-1 border-sky-200"  placeholder="Пошук..." type="text">

        <div class="services-list">
            <ServiceCard v-for="(service, i) in searchServices" :key="i" :service="service" />
        </div>
    </div>
</template>

<script setup>
import services from '~/content/services';
import ServiceCard from '~/components/ServiceCard.vue';

const search = ref('')

const searchServices = computed(() => {
    return services.filter((s) => {
        const searchString = (s.name + s.address + s.phones.join('') + s.categories.join('') + s.description).toLowerCase()
        return searchString.includes(search.value.toLowerCase())
    })
})
</script>

<style scoped>
    .services-list {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
    }
</style>