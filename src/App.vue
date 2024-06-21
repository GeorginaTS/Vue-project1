<template>
  <div class="flex flex-col  justify-center items-center">
    <Header class="w-full" />
    <div class="flex w-full gap-4">
      <SearchBar @searchStr="searchValue" @category="searchCategory" @minPrice="searchMinPrice" @maxPrice="searchMaxPrice" @orderBy="searchOrderBy" class="w-[18rem]" />
      <Detail :id="idSelected" :key="idSelected"  @idSelected="closeDetail" v-if="idSelected>0"/>
      <Grid :str="searchStr" :category="category" :minPrice="minPrice" :maxPrice="maxPrice" :orderBy="orderBy" @idSelected="showDetail" class="w-full" v-if="idSelected == 0" />  
      <Grid :str="searchStr" :category="category" :minPrice="minPrice" :maxPrice="maxPrice" :orderBy="orderBy" @idSelected="showDetail"  class="w-[16rem]" v-if="idSelected > 0"/>  
    </div>
  </div>

</template>
<script>
import Header from "./components/Header.vue"
import SearchBar from "./components/SearchBar.vue"
import Grid from "./components/GridProducts.vue"
import Detail from "./components/Detail.vue"

export default {
  name: "App",
  components: { Header, Grid, SearchBar, Detail },
  data() {
    return {
      title: "Best Store",
      searchStr: "",
      category: "0",
      minPrice: 0,
      maxPrice: 1000,
      orderBy: "title",
      idSelected:0
    }
  },
  methods: {
    searchValue(str) {
      this.searchStr = str
    },
    searchCategory(value) {
      this.category = value
    },
    searchMinPrice(value) {
      this.minPrice = value
    },
    searchMaxPrice(value) {
      this.maxPrice = value
    },
    searchOrderBy(value) {
      this.orderBy = value
    },
    showDetail(id) {
      this.idSelected = id
    },
    closeDetail(id) {
      this.idSelected = 0
    }
  }
}
</script>
