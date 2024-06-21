<template>
    <div>
       ⭐ {{ stars.rate }} ( {{stars.count }}valorations)
    </div>
</template>
<script>
export default {
    name:"StarRating",
    props: ["stars"],
    data() {
        return{

        }
    }   
}
</script>
<style>
    
</style>