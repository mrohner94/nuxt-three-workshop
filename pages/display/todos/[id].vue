<template>
  <h2>This is task id: {{ route.params }}</h2>
  <NuxtLink to="/display/todos"> Go Back </NuxtLink>
</template>
/
<script setup>
const route = useRoute();
</script>
