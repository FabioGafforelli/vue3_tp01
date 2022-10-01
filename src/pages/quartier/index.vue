<script setup lang="ts">
import groupBy from "lodash/groupBy";
import {Disclosure, DisclosureButton, DisclosurePanel} from "@headlessui/vue";
import { supabase } from "../../supabase";
    const { data, error } = await supabase.from("quartiercommune").select("*");
    if (error) console.log("n'a pas pu charger la table quartiercommune :", error);
    </script>
    
    <template>
      <section class="flex flex-col">
        <h3 class="text-2xl">Liste des quartiers</h3>
      <!--ul>
          <li v-for="quartierObject in (data as any[])">
            {{ quartierObject.libelle_Commune }} -
            {{ quartierObject.libelle_Quartier }}
          </li>
        </ul>  -->
        <Disclosure
    v-for="(listeQuartier, libelle_commune) in groupBy(
      data,
      'libelle_commune'
    )"
    :key="libelle_commune"
  >
  <DisclosureButton>
    {{libelle_commune}}
  </DisclosureButton>
  <DisclosurePannel>
          <li v-for="quartierObject in (listeQuartier as any[])">

            <RouterLink
  :to="{
    name: 'quartier-id',
    params: { id: quartierObject.libelle_quartier },
  }"
>{{ quartierObject.libelle_quartier }}</RouterLink>
          </li>
  </DisclosurePannel>
  </Disclosure>
      </section>
    </template>