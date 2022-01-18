<template>
  <select
    v-model="genreValue"
    @change="$emit('filterGnr', genreValue)"
    name="genres"
    id="genres"
  >
    <option value="" selected>Choose a genre:</option>
    <option value="rock">rock</option>
    <option value="pop">pop</option>
    <option value="jazz">jazz</option>
    <option value="metal">metal</option>
  </select>
</template>

<script>
export default {
  name: "Select",
  data() {
    return {
      genreValue: "",
    };
  },
  created() {},
};
</script>

<style>
/* #genres {

} */
</style>
