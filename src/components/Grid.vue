<template>
    <div class="">
        Products list
        <br>
        <ul class="flex flex-wrap h-fit gap-4 justify-center">
            <li v-for="item in content" :key="item.id">
             <Card :product="item"/>
            </li>
        </ul>
        
        {{ content }}
    </div>
</template>
<script>
import Card from "./Card.vue"
export default {
    name:"Grid",
    components: {Card},
    data() {
        return {
            content: []

        }
    },
    async mounted() {
      try {
        const response = await fetch(`https://fakestoreapi.com/products`);
        this.content = await response.json()
        console.log('Success');
      } catch {
        console.error('Failed');
      }

  }
    
}
</script>