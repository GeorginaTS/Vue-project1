<template>
    <div>
        <input type="text" name="searchStr" v-model="searchStr" class="border border-gray-800">
    </div>
</template>
<script>
export default {
    name: "SearchBar",
    data () {
        return {
            searchStr: ""

        }
    }, 
    watch: {
        searchStr(value) {
            console.log("searchStr", value)
            this.$emit('searchStr', value); 
        }
    }
    
}
</script>
<style>
    
</style>