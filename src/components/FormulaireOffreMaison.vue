<script setup lang="ts">
import { ref } from "@vue/reactivity"; 
import { supabase } from "@/supabase";
import Card from '@/components/Card.vue';
import { useRouter } from "vue-router";
const router = useRouter();
// On fait une variable réactive qui réference les données
    // ATTENTION : faire une Ref pas une Reactive car :
    // c'est l'objet qui doit être réactif, pas ses props
    const maison = ref({});
    const props = defineProps(["id"]);
if (props.id) {
 // On charge les données de la maison
 let { data, error } = await supabase
 .from("maison")
 .select("*")
 .eq("id", props.id);
 if (error) console.log("n'a pas pu charger le table Maison :", error);
 else maison.value = (data as any[])[0];
}
    async function upsertMaison(dataForm, node) {
 const { data, error } = await supabase.from("maison").upsert(dataForm);
 if (error) node.setErrors([error.message])
else {
        node.setErrors([]);
        router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}

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
        <FormKit  @submit="upsertMaison" type="form" :submit-attrs="{ classes: { input: 'bg-indigo-300 p-1 rounded' } }" :config="{
 classes: {
 input: 'p-1 rounded border-gray-300 shadow-sm border',
 label: 'text-gray-600',
 },
 }" v-model="maison">
            
           <FormKit name="titre" label="Nom" />
           <FormKit name="adresse" label="Adresse" />
           <FormKit name="surface" label="surface m²" />
           <FormKit name="price" label="Prix" type="number" />
           <FormKit name="nbrSDB" label="Nombre de salle de bain" type="number" />
           <FormKit name="nbrChambres" label="Nombre de chambres" type="number" />
           <FormKit name="favoris" label="Mettre en valeur"
          type="checkbox" wrapper-class="flex" :submit-attrs="{ classes: { input: 'bg-red-300 p-1 rounded' } }"
 />
          
        </FormKit>
     </div>
    </div>
</template>