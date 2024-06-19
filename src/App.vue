<template>
  <div class="flex flex-col  justify-center items-center">
    <Header class="w-full" />
    <div class="flex w-full gap-4">
      <searchBar @searchStr="searchValue" @category="searchCategory" class="w-[22rem]" />
      <Detail :id="idSelected"   @idSelected="closeDetail" v-if="idSelected>0" class="w-full"/>
      <Grid :str="searchStr" :category="category" @idSelected="showDetail"  class="w-full" v-if="idSelected == 0"/>  
      <Grid :str="searchStr" :category="category" @idSelected="showDetail"  class="w-[22rem]" v-if="idSelected > 0"/>  
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
    showDetail(id) {
      this.idSelected = id
    },
    closeDetail(id) {
      this.idSelected = 0
    }
  }
}
</script>
