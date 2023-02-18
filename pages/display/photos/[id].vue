<template>
  <h2 class="subtitle">This is photo id: {{ route.params.id }}</h2>

  <NuxtLink to="/display/photos"> Go Back </NuxtLink>
</template>
/
<script setup>
const route = useRoute();
</script>
