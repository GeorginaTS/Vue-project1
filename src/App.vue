<template>
    <div class="flex flex-col  justify-center items-center">
      <Header />
      <Grid />
    </div>

</template>
<script>
import Header from "./components/Header.vue"
import Grid from "./components/Grid.vue"

export default {
  name: "App",
  components: {Header, Grid},
  data() {
    return{
      title: "Best Store"
    }
  }
  
}
</script>
