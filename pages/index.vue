<template>
    <div>
        <h1>Українці в Колорадо | Послуги</h1>

        <input v-model="search" style="border-radius: 12px; height: 36px; margin-bottom: 16px; padding: 0 12px; width: 320px; border: 1px solid lightblue;" placeholder="Search..." type="text">

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
        console.log(searchString)
        return searchString.includes(search.value.toLowerCase())
    })
})
</script>

<style scoped>
    .services-list {
        display: flex;
        /* flex-direction: column; */
        gap: 12px;
        flex-wrap: wrap;
    }
</style>