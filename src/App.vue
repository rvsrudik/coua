<template>
  <div>
      <h1>Українці в Колорадо | Послуги</h1>

      <input style="border-radius: 12px; height: 36px; margin-bottom: 16px; padding: 0 12px; width: 320px; border: 1px solid lightblue;" placeholder="Search..." type="text">
      <div class="services-list">
          <ServiceCard v-for="(service, i) in services" :key="i" :service="service" />
      </div>
  </div>
</template>

<script setup>
import services from './content/services';
import ServiceCard from './components/ServiceCard.vue';
</script>

<style scoped>
  .services-list {
      display: flex;
      /* flex-direction: column; */
      gap: 12px;
      flex-wrap: wrap;
  }
</style>