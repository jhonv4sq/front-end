<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header class="pt-4 px-4 pb-4">
      <nav class="w-full flex justify-center gap-5 text-slate-400 ">
        <RouterLink to="/" exact>Home</RouterLink>
        <RouterLink to="/records" >Show Records</RouterLink>
      </nav>
  </header>

  <section class="w-full p-4">
    <RouterView />
  </section>
</template>

