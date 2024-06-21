<template>
    <div class="w-[18rem] flex  flex-col items-center justify-start p-4 gap-10 bg-neutral-200 rounded-r-xl h-full">
        <div>search bar</div>
        <div>
            <input type="text" name="searchStr" v-model="searchStr" class="w-48 border border-gray-800"
                placeholder="Enter word">
        </div>
        <hr>
        <div class="flex flex-col">
            Select a Category:
            <select name="category" id="category" v-model="category" class="capitalize w-48">
                <option value="0">All categories</option>
                <option :value="item" v-for="item in categories">{{ item }}</option>
            </select>
        </div>
        <hr>
        <div class="flex flex-col gap-2">
            Price range:
            <input type="number" v-model="minPrice" placeholder="min price">
            <input type="number" v-model="maxPrice" placeholder="max price">
        </div>
        <hr>
        <div class="flex flex-col gap-2">
            Order By:
            <select name="orderBy" id="orderBy" class="w-48">
                <option value="title">Title</option>
                <option value="price">Price</option>
            </select>
            <div class="flex justify-between p-2">
                <div>ASC 
                    <input type="radio" name="order" id="order" value="asc" class="w-4"></div>
                <div>DESC 
                    <input type="radio" name="order" id="order" value="desc" class="w-4"></div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "SearchBar",
    data() {
        return {
            searchStr: "",
            categories: "",
            category: "0",
            minPrice: "",
            maxPrice: ""
        }
    },
    watch: {
        searchStr(value) {
            this.$emit('searchStr', value);
        },
        category(value) {
            this.$emit('category', value);
        },
        minPrice(value) {
            this.$emit('minPrice', value)
        },
        maxPrice(value) {
            this.$emit('maxPrice', value)
        }
    },
    async mounted() {
        try {
            const response = await fetch(`https://fakestoreapi.com/products/categories`);
            this.categories = await response.json()
            console.log('Success');
        } catch {
            console.error('Failed');
        }
    }

}
</script>
<style scoped>
input,
select {
    color: black;
    background-color: white;
    border: 1px solid grey;
    border-radius:0.2rem;
}
hr {
    margin: 0;
    padding: 0;
    height: 2px;
    width:100%;
    background-color: lightgrey;

}
</style>