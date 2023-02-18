<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
</style>
<template>
  <NuxtLayout name="display">
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
  </NuxtLayout>
</template>
<script setup></script>
