<template>
    <div class="flex flex-col items-center w-full">
      <h3 class="w-[50%] text-center bg-neutral-200 rounded">Search string: {{str}} category: {{ category }}</h3>
        <h3 v-if="newContent.length == 0">NO hi ha cap producte seleccionat</h3>
        <br>
        <ul class="flex flex-wrap h-fit gap-4 justify-center">
            <li v-for="item in newContent" :key="item.id">
              <Card :product="item" @click="showDetail(item.id)"/>
            </li>
        </ul>
    </div>
</template>
<script>
import Card from "./Card.vue"
export default {
    name:"Grid",
    props: ["str", "category"],
    components: {Card},
    data() {
        return {
            content: [],
            newContent:[]

        }
    },
    async mounted() {
      try {
        const response = await fetch(`https://fakestoreapi.com/products`);
        this.content = await response.json()
        this.newContent = await this.content
        console.log('Success');
      } catch {
        console.error('Failed');
      }

    },
    watch: {
      str(value) {
        console.log("str value= ", value) 
        if (value !== "") {
            this.newContent = this.content.filter(e => e.title.toLowerCase().includes(value.toLowerCase()))
            
            if (this.category != "0") {
              console.log("category" , this.category)
              this.newContent = this.newContent.filter(e => e.category == this.category)
            }
            console.log(this.newContent)
        } else {
          this.newContent = this.content
          if (this.category != "0") {
              console.log("category" , this.category)
              this.newContent = this.newContent.filter(e => e.category == this.category)
          } 
        }
      },
      category(value) {
        console.log("category value= ", value) 
        if (value !== "0") {
            this.newContent = this.content.filter(e => e.category == value)
            if (this.str != "") {
              this.newContent = this.newContent.filter(e => e.title.toLowerCase().includes(this.str.toLowerCase()))
            }
            console.log(this.newContent)
        } else {
          this.newContent = this.content
          if (this.str != "") {
              this.newContent = this.newContent.filter(e => e.title.toLowerCase().includes(this.str.toLowerCase()))
            }
        }
      }
    },
    methods: {
      showDetail(id) {
        console.log("Grid showDetail", id)
        this.$emit('idSelected', id);
      }
    }
}
</script>