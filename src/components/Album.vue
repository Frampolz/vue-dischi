<template>
  <div class="album-box">
    <div class="album-cover">
      <img :src="src" :alt="title" />
    </div>
    <div class="album-details">
      <h2>{{ title }}</h2>
      <h3>{{ author }}</h3>
      <h4>{{ year }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "Album",
  props: {
    src: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style></style>
