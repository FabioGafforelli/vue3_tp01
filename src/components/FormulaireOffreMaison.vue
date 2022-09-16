<script setup lang="ts">

import { ref } from "@vue/reactivity"; 
import Card from '@/components/Card.vue'
// On fait une variable réactive qui réference les données
    // ATTENTION : faire une Ref pas une Reactive car :
    // c'est l'objet qui doit être réactif, pas ses props
    const maison = ref({});
</script>
<template>
    <div>
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
            <!-- Optionnel on affiche les données -->
            <Card v-bind="maison" />
        </div>
     <div class="p-2">
        <!-- On passe la "ref" à FormKit -->
           <FormKit name="nom" label="Nom" />
           <FormKit name="prix" label="Prix" type="number" />
           <FormKit name="nbrSDB" label="Nombre de salle de bain" type="number" />
           <FormKit name="favori" label="Mettre en valeur"
          type="checkbox" />
        </FormKit>
     </div>
    </div>
</template>