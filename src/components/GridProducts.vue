<template>
    <div class="flex flex-col items-center w-full">
      <h3 class="w-[50%] text-center bg-neutral-200 rounded">Search string:["{{str}}"] Category: {{ category }} orderBy: {{ orderBy}}</h3>
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
    props: ["str", "category", "minPrice", "maxPrice", "orderBy", "order"],
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
        if (this.str !== "") {
          this.newContent = await this.newContent.filter(e => e.title.toLowerCase().includes(this.str.toLowerCase()))
        }
        if (this.category !== "0") {
          this.newContent = await this.newContent.filter(e => e.category == this.category)
        }
        if (this.minPrice !== "" && this.minPrice > 0) {
          this.newContent = await this.newContent.filter(e => e.price > this.minPrice)
        }
        if (this.maxPrice !== "" && this.maxPrice > 0) {
          this.newContent = await this.newContent.filter(e => e.price < this.maxPrice)
        }
        //order
        if (this.orderBy == "price") {
          this.newContent = await this.newContent.sort((a,b) => a.price - b.price)
        } else {
          this.newContent = await this.newContent.sort((a,b) => {
            if (a.title > b.title) {
              return 1;
            }
            if (a.title < b.title) {
              return -1;
            }
            // a must be equal to b
            return 0;}
          )
        }
        console.log('Success');
      } catch {
        console.error('Failed');
      }

    },
    watch: {
      str(value) {
        this.updateContent()
      },
      category(value) {
        this.updateContent()
      },
      minPrice(value){
        this.updateContent()
      },
      maxPrice(value){
        this.updateContent()
      },
      orderBy(value){
        this.updateContent()
      }
    },
    methods: {
      showDetail(id) {
        console.log("Grid showDetail", id)
        this.$emit('idSelected', id);
      },
      updateContent() {
        if (this.str !== "") {
            this.newContent = this.content.filter(e => e.title.toLowerCase().includes(this.str.toLowerCase()))
            
            if (this.category != "0") {
              console.log("category" , this.category)
              this.newContent = this.newContent.filter(e => e.category == this.category)
            }
            if (this.minPrice !== "" && this.minPrice > 0) {
              this.newContent = this.newContent.filter(e => e.price > this.minPrice)
            }
            if (this.maxPrice !== "" && this.maxPrice > 0) {
              this.newContent =  this.newContent.filter(e => e.price < this.maxPrice)
            }
            console.log(this.newContent)
        } else {
          this.newContent = this.content
          if (this.category != "0") {
              console.log("category" , this.category)
              this.newContent = this.newContent.filter(e => e.category == this.category)
          }
          if (this.minPrice !== "" && this.minPrice > 0) {
              this.newContent = this.newContent.filter(e => e.price > this.minPrice)
          }
          if (this.maxPrice !== "" && this.maxPrice > 0) {
              this.newContent =  this.newContent.filter(e => e.price < this.maxPrice)
          }
        }
        //order
        if (this.orderBy == "price") {
          this.newContent = this.newContent.sort((a,b) => a.price - b.price)
        } else {
          this.newContent = this.newContent.sort((a,b) => {
            if (a.title > b.title) {
              return 1;
            }
            if (a.title < b.title) {
              return -1;
            }
            // a must be equal to b
            return 0;}
          )
        }
        
      }
    }
}
</script>