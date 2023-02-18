<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
</style>
<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <PhotoGallery />
        </div>
        <div class="column">
          <ToDoViewer />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import ToDoViewer from "./components/ToDoViewer.vue";
import PhotoGallery from "./components/PhotoGallery.vue";
</script>
