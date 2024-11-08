<template>
    <div class="p-10">
        <div class="flex justify-between items-center">
            <h2 class="text-3xl font-bold mb-10">All Sneakers</h2>
            <div class="flex gap-4">
                <select v-model="filters.sortBy" @change="onChangeSelect" name="sorting" class="py-2 px-3 border rounded-md outline-none">
                    <option value="title-asc">By Name (A - Z)</option>
                    <option value="title-desc">By Name (Z - A)</option>
                    <option value="price-asc">By Price (Lowest to Highest)</option>
                    <option value="price-desc">By Price (Highest to Lowest)</option>
                </select>
                <!-- <select @change="onChangeSelect" name="sorting" class="py-2 px-3 border rounded-md outline-none">
                    <option value="title-asc">By Name (A - Z)</option>
                    <option value="title-desc">By Name (Z - A)</option>
                    <option value="price">By Price (Lowest to Highest)</option>
                    <option value="-price">By Price (Highest to Lowest)</option>
                </select> -->
                <div class="relative">
                    <img src="/img/search.svg" alt="" class="absolute left-4 top-3">
                    <!-- <input @change="onChangeSearchInput" class="border focus:border-gray-400 rounded-md py-2 pl-11 pr-4 outline-none" type="text" placeholder="search..."> -->
                    <input v-model="filters.searchQuery" @change="onChangeSearchInput" class="border focus:border-gray-400 rounded-md py-2 pl-11 pr-4 outline-none" type="text" placeholder="search...">
                </div>
            </div>
        </div>
        <div class="mt-10">
            <div class="grid grid-cols-4 gap-5">
                <!-- <Card v-for="item in items" v-bind:key="item.id" :item="item" :onClickAdd="onClickAdd"/> -->
                <Card v-for="item in sortedAndFilteredItems" v-bind:key="item.id" :item="item" :onClickAdd="onClickAdd"/>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, defineProps, onMounted, computed ,watch } from 'vue'

import Card from '@/components/Card.vue'
import axios from 'axios'

defineProps({
    
})

const items = ref([])

const filters = ref({
    searchQuery: '',
    sortBy: 'title-asc'
})

const onChangeSelect = () => {
    filters.value.sortBy = filters.value.sortBy
}

const onChangeSearchInput = () => {
    filters.value.searchQuery = filters.value.searchQuery
}

const sortedAndFilteredItems = computed(() => {
    let filteredArray = items.value.filter(item => 
    item.title.toLowerCase().includes(filters.value.searchQuery.toLocaleLowerCase())
    )

    if (filters.value.sortBy === 'title-asc') {
        return filteredArray.sort((a, b) => a.title.localeCompare(b.title))
    } else if (filters.value.sortBy === 'title-desc') {
        return filteredArray.sort((a, b) => b.title.localeCompare(a.title))
    } else if (filters.value.sortBy === 'price-asc') {
        return filteredArray.sort((a, b) => a.price - b.price)
    } else if (filters.value.sortBy === 'price-desc') {
        return filteredArray.sort((a, b) => b.price - a.price)
    } else {
        return filteredArray
    }
})

const fetchFavourites = async () => {
    try{
        const { data: favourites } = await axios.get(`https://70e0dec5c69ca79f.mokky.dev/favourites`)
        items.value = items.value.map(item => {
            const favourite = favourites.find(favourite => favourite.parentId === item.id)

            if(!favourite){
                return item
            }

            return {
                ...item,
                isFavourite: true,
                favouriteId: favourite.id
            }
        })
    } catch(error){
        console.error('Error fetching data AKA kesalahan berpikir', error)
    }
}

const fetchItems = async () => {
    try{
        const params = {
            sortBy: filters.value.sortBy
        }

        if(filters.value.searchQuery){
            params.title = `*${filters.value.searchQuery}*`
        }

        const response = await axios.get(`https://70e0dec5c69ca79f.mokky.dev/items`, {
            params
        })
        items.value = response.data.map((obj) => ({
            ...obj,
            isFavourite: false,
            isAdded: false
        }))
    } catch(error){
        console.error('Error fetching data AKA kesalahan berpikir', error)
    }
}

onMounted(async () => {
    await fetchItems()
    await fetchFavourites()
})
watch(filters.value, fetchItems)

const onClickAdd = () => {
    alert('Alerta Maxima')
}
</script>

<!-- <script setup>
import { ref, defineProps, onMounted, computed ,watch } from 'vue'

import Card from '@/components/Card.vue'
import axios from 'axios'

const items = ref([])

const filters = ref({
    searchQuery: '',
    sortBy: ''
})

const onChangeSelect = (event) => {
    filters.value.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
    filters.value.searchQuery = event.target.value
}

const fetchItems = async () => {
    try{
        const params = {
            sortBy: filters.value.sortBy
        }

        if(filters.value.searchQuery){
            params.title = `*${filters.value.searchQuery}*`
        }

        const response = await axios.get(`https://70e0dec5c69ca79f.mokky.dev/items`, {
            params
        })
        items.value = response.data
    } catch(error){
        console.error('Error fetching data AKA kesalahan berpikir', error)
    }
}

onMounted(fetchItems)

watch(filters.value, fetchItems)

const onClickAdd = () => {
    alert('Alerta Maxima')
}
</script> -->

<style scoped>

</style>