<template>
    <div>
        <h1 class="text-3xl w-full text-center font-extrabold p-4 text-emerald-600">{{ title }}</h1> 
        <nav>
            <ul class="flex justify-around">
                <li>Home</li>
                <li>Products</li>
                <li>contact</li>
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
<style>
</style>
