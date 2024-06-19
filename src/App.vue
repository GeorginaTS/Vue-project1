<template>
  <div class="flex flex-col  justify-center items-center">
    <Header />
    <div class="flex w-full">
      <searchBar @searchStr="searchValue" @category="searchCategory" class="w-[25%] min-w-56" />
      <Grid :str="searchStr" :category="category" class="w-[75%]" />
    </div>

  </div>

</template>
<script>
import Header from "./components/Header.vue"
import SearchBar from "./components/SearchBar.vue"
import Grid from "./components/Grid.vue"

export default {
  name: "App",
  components: { Header, Grid, SearchBar },
  data() {
    return {
      title: "Best Store",
      searchStr: "",
      category: "0"
    }
  },
  methods: {
    searchValue(str) {
      this.searchStr = str
    },
    searchCategory(value) {
      this.category = value
    }
  },
  watch: {
    searchStr(value) {

    },
    category(value) {

    }
  }

}
</script>
