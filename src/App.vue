<template>
  <nav>
    <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul>
      <li>
        <router-link class="text-red-600 underline" to="/">
          lien vers
          <code class="font-mono">/src/pages/index.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/simple">
          lien vers
          <code class="font-mono">la liste simple</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste">
          lien vers
          <code class="font-mono">la liste des maisons</code>
        </router-link>
      </li>
        <li>
          <router-link class="text-red-600 underline" to="/listeFetch">
          lien vers
          <code class="font-mono">liste fetch</code>
        </router-link>
        </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/new">
          lien vers
          <code class="font-mono">le formulaire</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste-supabase">
          lien vers
          <code class="font-mono">liste-supabase</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/login-logout">
          Login/logout
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/new">
          Nouvelle maison
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/[id]">
          Editer la maison
        </router-link>
      </li>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
  <router-view class="m-2 border-2 p-2" />
</Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from '@heroicons/vue/20/solid'
import { supabase } from './supabase';
</script>
