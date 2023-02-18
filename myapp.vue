<style lang="scss">
  @import './node_modules/bulma/bulma.sass';
  .photo-gallery-list {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
  }
</style>
<template>
  <div class="container">
    <div class="section">
      <h1 class="title">Photo Gallery</h1>
        <h4>{{ numberOfPhotos }} photos</h4>
        <button @click="fetchPhotoGallery">Fetch Data</button>
        <ul class="photo-gallery-list">
          <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
            <img :src="photo.thumbnailUrl" :alt="photo.title">
          </li>
        </ul>
    </div>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
const photoGallery = ref([])

const fetchPhotoGallery = () => {
  console.log('fetching')
  fetch('https://jsonplaceholder.typicode.com/photos/').then((response) => {
    response.json().then((res) => {
      photoGallery.value = res;
    });
  })
}

const numberOfPhotos = computed(() => {
  return photoGallery.value.length;
})
</script>