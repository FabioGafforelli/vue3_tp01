<template>
    <div class="p-2">
        <h1 class="text-2xl">Page Liste Supabase</h1>
        <div v-for="maison in tableauDesMaisons" :key="maison.nomMaison">
            <Card class="w-1/2" v-bind="maison"/> 
        </div>
    </div>
</template>

<script setup lang="ts">
import Card from "@/components/Card.vue";
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
// const maisons = []; // à remplacer par l'appel à Supabase

let { data: tableauDesMaisons } = await supabase
  .from('maison')
  .select('*')

console.log(tableauDesMaisons)

</script>
