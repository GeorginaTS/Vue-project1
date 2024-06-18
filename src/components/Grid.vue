<template>
    <div class="">
        Search string: {{str}}
        <br>
        <ul class="flex flex-wrap h-fit gap-4 justify-center">
            <li v-for="item in newContent" :key="item.id">
             <Card :product="item"/>
            </li>
        </ul>
    </div>
</template>
<script>
import Card from "./Card.vue"
export default {
    name:"Grid",
    props: ["str"],
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
            this.newContent = this.content.filter(e => e.title.toLowerCase().includes(value))
            console.log(this.newContent)
        } else {
          this.newContent = this.content
        }
    }
  }
}
</script>