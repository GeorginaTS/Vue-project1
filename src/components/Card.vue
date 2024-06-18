<template>
    <div class="border border-blue-600 w-64 h-full rounded-lg p-2">
        <img :src="product.image" :alt="product.title">
     {{ product.title }} - {{ product.price }}
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