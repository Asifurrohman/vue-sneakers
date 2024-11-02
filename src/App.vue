<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <!-- <Header/> -->
    
    <!-- <div class="p-10"> -->
      <!-- <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-10">All Sneakers</h2>
        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none">
            <option value="name">By Name</option>
            <option value="cheapest">By Price (Cheap)</option>
            <option value="mostExpensive">By Price (Expensive)</option>
          </select>
          <div class="relative">
            <img src="/img/search.svg" alt="" class="absolute left-4 top-3">
            <input class="border focus:border-gray-400 rounded-md py-2 pl-11 pr-4 outline-none" type="text" placeholder="search...">
          </div>
        </div>
      </div> -->
      <!-- <div class="mt-10"> -->
        <!-- <CardList/> -->
      <!-- </div> -->
    <!-- </div> -->
    <RouterView></RouterView>
  </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'

import  Header from '@/components/Header.vue'
import  CardList from '@/components/CardList.vue'
import  Drawer from '@/components/Drawer.vue'
</script>

<style scoped>

</style>