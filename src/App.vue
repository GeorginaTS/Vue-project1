<template>
  <div class="flex flex-col  justify-center items-center">
    <Header class="w-full" />
    <div class="flex w-full gap-4">
      <searchBar @searchStr="searchValue" @category="searchCategory" class="w-32 min-w-64" />
      <Grid :str="searchStr" :category="category" @idSelected="showDetail" v-if=" idSelected == 0"/>
      <Detail :id="idSelected"   @idSelected="closeDetail" v-if="idSelected>0"/>
    </div>

  </div>

</template>
<script>
import Header from "./components/Header.vue"
import SearchBar from "./components/SearchBar.vue"
import Grid from "./components/Grid.vue"
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
