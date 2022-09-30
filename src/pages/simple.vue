<template>
<h1>Page simple</h1>
<Card v-bind="objet"/>
</template>

<script setup lang="ts">
    import Card from '../components/Card.vue';
    const objet = {price:"2000", titre:"Beverly Springfield", image:"/public/maison1.jpg", lieu:"2821 Lake Sevilla, Palm Harbor, TX", nbrSDB:"3", }
</script>
