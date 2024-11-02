<template>
    <div class="relative bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl">
        <img :src="!isFavourite ? '/img/like-1.svg' : '/img/like-2.svg'" @click="onClickFavourite" alt="" class="absolute top-0 left-0">
        <img :src="item.imageUrl" alt="">
        <p class="mt-2">
            {{ item.title }}
        </p>
        <div class="flex justify-between mt-5">
            <div class="flex flex-col">
                <span class="text-slate-400">Price:</span>
                <b>Rp.{{ item.price }}</b>
            </div>
            <img :src="!isAdded ? '/img/plus.svg' : '/img/checked.svg'" alt="" @click="onClickAdd">
        </div>
    </div>
</template>

<script setup>
import { defineProps, ref, computed } from 'vue'

defineProps({
    item: Object,
    imageUrl: String,
    title: String,
    price: Number,
    isFavourite: Boolean,
    isAdded: Boolean,
    onClickAdd: Function,
    onClickFavourite: Function
})
</script>

<style scoped>

</style>