<script setup lang="ts">
    import Card from "../components/Card.vue";

 // const maisons = [{nom:"test", price:34, favoris:true, txt:"produit de test", nbbath:2, nbsize:"test m²", img:"/public/card.jpg"}, {nom:"test2", price:27, favoris:false, txt:"2ème produit de test", nbbath:2, nbsize:"test*2 m²", img:"/public/card.jpg"}, {nom:"Dernier test", price:86, txt:"Dernier produit de test", nbbath:1, nbsize:"test m²", img:"/public/card.jpg"}]
    import maisons from "../assets/maisons.json";
</script>

<template>
    <div class="p-2">
        <h1 class="text-2xl">Page Liste</h1>
        <Card v-for="maison in maisons" :key="maison.titre" v-bind="maison"/>
            <!--<card class="w-1/2" v-bind="maisons"/>-->
    </div>
</template>