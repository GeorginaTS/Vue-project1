<template>
    <div class="w-full flex justify-between items-center">
        <div>
            <img src="../assets/img/Best.png" alt="Logo" class="h-32">
        </div> 
        <nav class="w-96 border border-slate-400 mr-10">
            <ul class="w-full flex justify-between">
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
    padding: 0 2rem;
}
li {
    text-transform: uppercase;
    padding: 0.5rem;
    font-weight: bold;
}
</style>
