<template>
    <div class="border border-neutral-300 w-64 h-full rounded-lg p-2 flex flex-col justify-center items-center">
        <img :src="product.image" :alt="product.title" class="w-[75%] max-h-56">
        <hr />
        <span class="font-bold">{{ product.title }}</span>{{ product.price }}€
    </div>
</template>
<script>
export default {
    name: "Card",
    props:["product"],
    data() {
        return {

        }
    }
    
}
</script>
<style>

</style>