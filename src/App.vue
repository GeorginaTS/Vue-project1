<template>
    <div class="flex flex-col  justify-center items-center">
      <Header />
      <searchBar @searchStr="searchValue"/>
      <Grid  :str="searchStr"/>
      
    </div>

</template>
<script>
import Header from "./components/Header.vue"
import SearchBar from "./components/SearchBar.vue"
import Grid from "./components/Grid.vue"

export default {
  name: "App",
  components: {Header, Grid, SearchBar},
  data() {
    return{
      title: "Best Store",
      searchStr: ""
    }
  }, 
  methods: {
    searchValue(str) {
      this.searchStr = str
    }
  },
  watch: {
    searchStr(value){

    }
  }
  
}
</script>
