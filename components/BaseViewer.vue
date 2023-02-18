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
    <button @click="fetchItemList">Fetch Data</button>
    <slot name="metrics" />
    <slot name="items" :itemList="itemList" />
  </div>
</template>
<script setup>
const props = defineProps({
  itemList: {
    type: Array,
    default: () => [],
  },
  title: {
    type: String,
    required: true,
  },
  itemType: {
    type: String,
    required: true,
  },
});

const emit = defineEmits(["update:itemList"]);

const fetchItemList = () => {
  fetch(`https://jsonplaceholder.typicode.com/${props.itemType}/`).then(
    (response) => {
      response.json().then((res) => {
        // itemList.value = res;
        emit("update:itemList", res);
      });
    }
  );
};
</script>
