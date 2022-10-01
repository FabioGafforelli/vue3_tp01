<script setup lang="ts">
    import {supabase} from "@/supabase"
import FormulaireCommune from "../../components/FormulaireCommune.vue"
    defineProps({
            id: String,
        })
    
    
    </script>
    
    <template>
        <div>
     
            <FormulaireCommune :id="id" />
        </div>
     
    </template>