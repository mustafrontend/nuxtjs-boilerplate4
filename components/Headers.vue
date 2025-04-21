<script setup>
const goToAbout = () => {
  navigateTo('/hakkimizda')
}
</script>

<template>
  <button @click="goToAbout">Hakkımızda'ya Git</button>
  <NuxtLink to="/hakkimizda">Hakkımızda</NuxtLink>

</template>
