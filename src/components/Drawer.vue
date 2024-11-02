<template>
    <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70">
        
    </div>
    <div class="fixed top-0 right-0 bg-white w-96 h-full z-20 p-8">
        <DrawerHead />
        <CartItemList />

        <div class="flex flex-col gap-4 mb-6 my-6 mt-7">
            <div class="flex gap-2">
                <span>Total:</span>
                <div class="flex-1 border border-dashed"></div>
                <b>Rp.2000000</b>
            </div>
            <div class="flex gap-2">
                <span>Tax (10%):</span>
                <div class="flex-1 border border-dashed"></div>
                <b>Rp.200000</b>
            </div>
        </div>
        <button disabled class="bg-lime-500 hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300 mt-4 transition w-full rounded-xl py-3 text-white cursor-pointer">
            Place an order
        </button>
    </div>
</template>

<script setup>
import DrawerHead from '@/components/DrawerHead.vue'
import CartItemList from '@/components/CartItemList.vue'
</script>

<style scoped>

</style>