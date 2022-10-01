<script setup lang="ts">
    import { ref } from "@vue/reactivity"; 
    import { supabase } from "@/supabase";
    import { useRouter } from "vue-router";
    const router = useRouter();
    // On fait une variable réactive qui réference les données
        // ATTENTION : faire une Ref pas une Reactive car :
        // c'est l'objet qui doit être réactif, pas ses props
        const commune = ref({});
        const props = defineProps(["id"]);
    if (props.id) {
        // On charge les données de la maison
        let { data, error } = await supabase
            .from("commune")
            .select("*")
            .eq("code_commune", props.id);
        if (error) console.log("n'a pas pu charger le table commune :", error);
        else commune.value = (data as any[])[0];
    }
        async function upsertcommune(dataForm, node) {
     const { data, error } = await supabase.from("commune").upsert(dataForm);
     if (error) node.setErrors([error.message])
    else {
            node.setErrors([]);
            router.push({ name: "edit-id", params: { id: data[0].id } });
        }
    }
    
    </script>
    <template>
        <div>
            <!-- On passe la "ref" à FormKit -->
            <FormKit  @submit="upsertcommune" type="form" :submit-attrs="{ classes: { input: 'bg-indigo-300 p-1 rounded' } }" :config="{
     classes: {
     input: 'p-1 rounded border-gray-300 shadow-sm border',
     label: 'text-gray-600',
     },
     }" v-model="commune">
                
               <FormKit name="libelle_commune" label="Nom de la commune" />

             
            </FormKit>
         </div>
    </template>