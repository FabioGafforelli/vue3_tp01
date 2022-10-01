<script setup lang="ts">
    import {supabase} from "@/supabase"
import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
const props = defineProps<{ id: string }>();


    
    </script>
    
    <template>
        <div>
     
            <FormulaireOffreMaison :id="Number(id)" />
        </div>
     
    </template>