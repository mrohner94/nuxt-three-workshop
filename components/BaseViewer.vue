<style lang="scss" scoped>
@import "./node_modules/bulma/bulma.sass";
@import "./assets/styles/main.scss";
.heading {
  color: $textColor;
}
</style>
<template>
  <div class="section">
    <slot name="hero" />
    <h1 class="title">{{ title }}</h1>
    <slot name="metrics" />
    <slot name="items" :itemList="itemList" />
  </div>
</template>
<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const itemType = route.path.split("/")[2];

const props = defineProps({
  itemList: {
    type: Array,
    default: () => [],
  },
  title: {
    type: String,
    required: true,
  },
});

const emit = defineEmits(["update:itemList"]);

const fetchItemList = () => {
  fetch(`https://jsonplaceholder.typicode.com/${itemType}/`).then(
    (response) => {
      response.json().then((res) => {
        // itemList.value = res;
        emit("update:itemList", res);
      });
    }
  );
};
onMounted(() => {
  fetchItemList();
});
</script>
