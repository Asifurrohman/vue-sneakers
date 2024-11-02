<template>
    <header class="flex justify-between border-b border-slate-200 px-10 py-8">
        <div class="flex items-center gap-4">
            <img src="/img/logo.png" alt="" class="w-10">
            <div>
                <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
                <p class="text-slate-400">Lorem ipsum dolor sit amet.</p>
            </div>
        </div>
        <ul class="flex items-center gap-8">
            <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
                <img src="/img/cart.svg" alt="">
                <b>Rp.50000</b>
            </li>
            <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
                <img src="/img/heart.svg" alt="">
                <span>Favourite</span>
            </li>
            <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
                <img src="/img/profile.svg" alt="">
                <span>Profile</span>
            </li>
        </ul>
    </header>
</template>

<script setup>

</script>

<style scoped>

</style>