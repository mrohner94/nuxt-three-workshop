<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
<template>
  <div class="section">
    <h1>Photo Gallery</h1>
    <NuxtPage v-if="route.params.id" />
    <BaseViewer v-else title="Photo Gallery" v-model:item-list="photoGallery">
      <template v-slot:metrics>
        <div>{{ filteredPhotoGallery.length }} photos</div>
      </template>
      <template v-slot:items>
        <ul class="photo-gallery-list">
          <li
            v-for="photo in filteredPhotoGallery"
            :key="`photo-id-${photo.id}`"
          >
            <NuxtLink :to="`/display/photos/${photo.id}`">
              <img :src="photo.thumbnailUrl" :alt="photo.title" />
            </NuxtLink>
          </li>
        </ul>
      </template>
    </BaseViewer>
  </div>
</template>
<script setup>
import { ref, computed } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const photoGallery = ref([]);

const numberOfPhotos = computed(() => {
  return photoGallery.value.length;
});

const filteredPhotoGallery = computed(() => {
  if (route.query.even) {
    return photoGallery.value.filter((photo) => photo.albumId % 2 === 0);
  }
  return photoGallery.value;
});
</script>
