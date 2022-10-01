<template>
    <figure>
        <img src="/public/maison1.jpg" alt="house" class="" >       
         <figcaption class="flex flex-col relative px-5 py-7 border-2 border-t-0 rounded-b-lg">
            <h3 class="text-2xl text-gray-900">{{ titre }}</h3>
            <address class="not-italic text-gray-500">{{ adresse }}</address>
            <div class="order-first flex items-center">
                <div class="text-2xl text-indigo-500">${{ price }}</div>
                <div class="text-gray-500 ">/months</div>
            </div>
            <hr class="border-indigo-100 border-t-2 my-2"/>
            <div class="flex justify-between text-sm">
                <div><bed class="inline-block align-top"/> {{nbrChambres}} </div>
                <div><bath class="inline-block align-top"/> {{ nbrSDB }} Bathrooms </div>
                <div><dimension class="inline-block align-top"/> {{surface}} m² </div>
            <div class="grid place-items-center w-12 h-12 border-2 border-indigo-100 rounded-full absolute top-7 right-5">
                <heart :class="{'fill-indigo-500': favoris}"/>
            </div>
            </div>
        </figcaption>
    </figure>
</template>

<script setup lang="ts">
import bed from "./icones/Bed.vue"
import bath from "./icones/Bath.vue"
import dimension from "./icones/Dimension.vue"
import heart from "./icones/Heart.vue"

defineProps({
    titre: {type:String, default:'Beverly Springifeld'},
    adresse: {type:String, default:'rue du test' },
    image: {type:String, default:'./public/maison1.jpg'},
    price: {type:Number, default:'123'},
    nbrChambres: {type:Number, default:''},
    nbrSDB: {type:Number, default:'2'},
    surface: {type:Number, default:'175 '},
    favoris: {type:Boolean, default:'False'},
})

</script>