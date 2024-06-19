<template>
    <div class="w-full">
        <h1 class="text-3xl w-full text-center font-extrabold p-4 text-emerald-600">{{ title }}</h1> 
        <nav class="w-full">
            <ul class="w-full flex justify-around">
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
<style scoped>
ul {
    padding: 1rem;
}
li {
    border: 1px solid green;
    padding:  0.5rem 1rem;
    border-radius: 0.5rem; 
    font-weight: bold;
    text-transform: uppercase;
}
</style>
