<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
<template>
  <BaseViewer
    title="Photo Gallery"
    itemType="photos"
    v-model:item-list="photoGallery"
  >
    <template v-slot:metrics>
      <div>{{ filteredPhotoGallery.length }} photos</div>
    </template>
    <template v-slot:items>
      <ul class="photo-gallery-list">
        <li v-for="photo in filteredPhotoGallery" :key="`photo-id-${photo.id}`">
          <img :src="photo.thumbnailUrl" :alt="photo.title" />
        </li>
      </ul>
    </template>
  </BaseViewer>
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
