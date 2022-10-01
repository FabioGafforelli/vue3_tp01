<script setup lang="ts">
import groupBy from "lodash/groupBy";
import {Disclosure, DisclosureButton, DisclosurePanel} from "@headlessui/vue";
import { supabase } from "../../supabase";
    const { data, error } = await supabase.from("quartiercommune").select("*");
    if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
    </script>
    
    <template>
      <section class="flex flex-col">
        <h3 class="text-2xl">Liste des Communes</h3>
        <Disclosure
    v-for="(listeCommune, libelle_commune) in groupBy(
      data,
      'libelle_commune'
    )"
    :key="libelle_commune"
  >

  <DisclosurePannel>
          <li v-for="communeObject in (listeCommune as any[])">

            <RouterLink
  :to="{
    name: 'commune-id',
    params: { id: communeObject.code_commune },
  }"
>{{ communeObject.libelle_commune }}</RouterLink>
          </li>
  </DisclosurePannel>
  </Disclosure>
      </section>
    </template>