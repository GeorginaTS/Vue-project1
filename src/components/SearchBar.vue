<template>
    <div class="w-full flex  flex-col items-center justify-start p-4 gap-10 bg-neutral-200 rounded-r-xl">
        <div>
            <input type="text" name="searchStr" v-model="searchStr" class="border border-gray-800" placeholder="Enter word"> <span
                class="bg-white p-1">🔎</span>
        </div>
        <div> Select a Category: 
            <select name="category" id="category" v-model="category">
                <option value="0">All categories</option>
                <option :value="item" v-for="item in categories">{{item}}</option>
            </select>
        </div>
    </div>
</template>
<script>
export default {
    name: "SearchBar",
    data() {
        return {
            searchStr: "",
            categories:"",
            category: "0"

        }
    },
    watch: {
        searchStr(value) {
            console.log("searchStr", value)
            this.$emit('searchStr', value);
        },
        category(value) {
            this.$emit('category', value);
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
div {
    color: white;
}
input, select {
    color: black;
    background-color: white;
}
</style>