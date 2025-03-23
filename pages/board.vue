<template>
        <div class="py-3">
            Для додавання оголошення напишіть на пошту  <a href="mailto:rvsrudik@gmail.com" class="underline text-blue-800">rvsrudik@gmail.com</a> або в телеграм <a href="https://t.me/vrudenko" class="underline text-blue-800">@vrudenko</a> 
        </div>

        <div>
            <div class="p-4 border-orange-500 border-1 rounded-xl w-full">
                <h3 class="mb-4 font-bold text-2xl">Здача квартири в оренду</h3>
                Здаємо кімнату у Westminsteri для однієї людини. Ціна $850 + комунальні послуги. Депозит $500.


                <div class="mt-3">
                    <b class="mt-1">    Оксана <a href="tel:+858-568-3360" class="ml-2 underline text-blue-800">+380123456789</a> </b>
                </div>
                
                <div class="flex flex-wrap gap-3 mt-4">
                <ImageViewer class="rounded-lg"  width="100px" height="100px" src="/img/1.jpeg" alt=""/>
                <ImageViewer class="rounded-lg"  width="100px" height="100px" src="/img/2.jpeg" alt=""/>
                <ImageViewer class="rounded-lg"  width="100px" height="100px" src="/img/3.jpeg" alt=""/>
                <ImageViewer class="rounded-lg"  width="100px" height="100px" src="/img/4.png" alt=""/>
            </div>
            </div>
        </div>
</template>

<script setup>
import ImageViewer from '~/components/ImageViewer.vue';

useHead({
  title: 'Українці в Колорадо | Дошка оголошень',
  meta: [
    { name: 'description', content: 'Платформа для українців у Колорадо, яка дозволяє знаходити та додавати послуги й сервіси в різних сферах, таких як ремонт, освіта, медицина, доставка, юридична допомога, ІТ-послуги та багато іншого.' }
  ]
})
</script>