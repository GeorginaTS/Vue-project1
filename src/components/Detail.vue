<template>
    <div class="w-full border border-neutral-300 p-4 rounded-l-xl flex flex-col items-center">
        <button @click="close" class="text-rose-700 underline">x close</button><br>
      <h3>{{ product.title }} : {{ product.price}}€</h3> 
      <img :src="product.image" :alt="product.title" class="w-[50%]">
      <hr class="w-full bg-neutral-400 h-[1px] my-8">
      <StarRating :stars="product.rating" v-if="product.rating"/>
      <br>
      <p>{{product.description}}</p>
    </div>
</template>
<script>
import StarRating from "./StarRating.vue"
export default {
    name: "Detail",
    data() {
        return {
            product: {}
        }
    },
    props: ["id"],
    components: {StarRating},
    methods: {
        close() {
            this.$emit('idSelected', 0);
        }

    },
    async created() {
      try {
        if (this.id > 0) {
            const res = await fetch(`https://fakestoreapi.com/products/${this.id}`);
            this.product = await res.json()
            console.log('Success', this.id);
        } else {
            console.log("id = 0")
        }

      } catch {
        console.error('Failed');
      }

    }, 
    watch: {
       async id(value) {
            try {
                if (value > 0) {
                    const res = await fetch(`https://fakestoreapi.com/products/${value}`);
                    this.product = await res.json()
                    console.log('Success', value);
                } else {
                    console.log("id <= 0")
                }

            } catch {
                console.error('Failed');
            }
        }
    }
}
</script>
<style>
    h3 {
        font-weight: bold;
        margin-bottom: 2rem;
    }
</style>