<template>
  <div class="p-2">
      <h1 class="text-2xl">Page Liste Supabase</h1>
      <div v-for="maison in tableauDesMaisons" :key="maison.nomMaison">
          <card class="w-1/2" v-bind="maison"/> 
      </div>
  </div>
</template>

<script setup lang="ts">

import card from "../components/Card.vue"
import { supabase } from "../supabase";
import FormulaireOffreMaison from "../components/FormulaireOffreMaison.vue";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
// const maisons = []; // à remplacer par l'appel à Supabase

let { data: tableauDesMaisons, error } = await supabase
.from('maison')
.select('*')

console.log(tableauDesMaisons)

</script>