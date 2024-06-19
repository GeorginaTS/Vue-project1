<template>
    <div class="w-full flex justify-between items-center">
        <div>
            <img src="../assets/img/Best.png" alt="Logo" class="h-32">
        </div> 
        <nav class="w-96 border border-neutral-300 mr-10 rounded-lg bg-neutral-200">
            <ul class="w-full flex justify-between">
                <li>Home</li>
                <li>Products</li>
                <li @click="showCart">🛒 cart</li>
            </ul>
        </nav>      
    </div>
</template>
<script>
export default {
    name: "Header",
    data() {
        return {
            title: "Best Shop"
        }
    }
}
</script>
<style scoped>
ul {
    padding: 0 2rem;
}
li {
    text-transform: uppercase;
    padding: 0.5rem;
    font-weight: bold;
}
</style>
