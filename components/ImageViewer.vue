<template>
    <img  v-bind="$attrs" :class="[isZoom ? '-is-zoom' : '']" @click="isZoom = !isZoom" style="max-height: 100px; width: auto; height: auto; " />
    <div v-if="isZoom" class="fixed inset-0 bg-[#000000e8]  w-full h-full top-0 left-0 flex items-center justify-center z-[100]"  @click="isZoom = !isZoom">
        <img v-bind="$attrs" :class="[isZoom ? '-is-zoom' : '']" class="w-auto h-auto max-h-full max-w-full object-cover"/>
    </div>
</template>

<script setup>

const isZoom = ref(false)
</script>