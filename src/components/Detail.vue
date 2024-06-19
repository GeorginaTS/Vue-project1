<template>
    <div class="w-[90%] border border-neutral-300 p-4 rounded-l-xl">
        <button @click="close" class="text-rose-700 underline">x close</button><br>
      <span class="text-xs text-neutral-400">{{ id }}</span>   
      <h3>{{ product.title }} : {{ product.price}}€</h3> 
      <img :src="product.image" :alt="product.title"> 
      <p>{{product.description}}</p>
      <br>
      <hr><br>
        <div class="text-xs">{{ product }}</div>
    </div>
</template>
<script>
export default {
    name: "Detail",
    data() {
        return {
            product: {}
        }
    },
    props: ["id"],
    methods: {
        close() {
            this.$emit('idSelected', 0);
        }

    },
    async mounted() {
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
                    console.log("id = 0")
                }

            } catch {
                console.error('Failed');
            }
        }
    }
}
</script>
<style>
    
</style>