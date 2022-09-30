<script setup lang="ts">
    import Card from '@/components/Card.vue';
        const res = await fetch("maisons.json");
        const maisons = await res.json();
    
    </script>
<template>
    <div class="p-2">
        <h1 class="text-2xl">Page Liste Fetch</h1>
        <div v-for="maison in maisons" :key="maison.nom">
           <card class="w-1/2" v-bind="maison"/>
        </div>
    </div>
</template>
