<template>
<div class="service-card">
    <div class="display: flex;">
        <h4 style="margin: 0; background-color: #e4ecef; color: #0f0f0f; width: fit-content; padding: 4px 12px; border-radius: 32px;" v-for="(category, i) in  service.categories" :key="i"> {{ category }} </h4>
    </div>
    
    <!-- <div style="display: flex; align-items: center; gap: 12px;"> -->
    <h3> {{ service.name  }} </h3>
    <p v-if="service.phones.length" class="display: flex; gap: 4">
        <a v-for="(phone, i) in service.phones" :key="i" :href='`tel:${phone}`'>{{phone}}</a> 
    </p>

    <p v-if="service.description">{{  service.description  }}</p>
    <!-- </div> -->

</div>
</template>

<script setup>

defineProps({
    service: {}
})
</script>

<style scoped>
.service-card {
    padding: 16px;
    /* border: 1px solid rgb(214, 213, 213); */
    border: 1px solid lightblue;
    border-radius: 12px;
    width: fit-content;
    max-width: 280px;

}
</style>