<template>
    <div class="flex justify-between w-full">
        <div id="stars" class="flex"> </div>
        <div>{{ stars.rate }} ( {{stars.count }} opinions)</div>
    </div>
</template>
<script>
export default {
    name:"StarRating",
    props: ["stars"],
    data() {
        return{

        }
    },
    computed: {
        roundStars() {
            return Math.round(this.stars.rate)
        }
    },
    mounted() {
        
         const starsDiv = document.getElementById("stars")
         console.log("mounted", starsDiv )
        for(let i =0; i < this.roundStars ; i++) {
            let star = document.createElement("div")
            //star.innerText = "star"
            star.innerHTML ="⭐"
            starsDiv.appendChild(star);
        }  
     } 
}
</script>
<style>
    
</style>