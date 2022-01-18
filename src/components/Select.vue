<template>
  <div>
    <select v-model="genreValue" @change="$emit('filterGnr',genreValue)" name="genres" id="genres">
  <option disabled value="">Choose a genre:</option>
      <option value="rock">rock</option>
      <option value="pop">pop</option>
      <option value="jazz">jazz</option>
      <option value="metal">metal</option>
</select>
  </div>
</template>

<script>
export default {
  name: "Select",
  data() {
    return {
      genreValue: ""
    }

  },
  created() {
  
  }
};
</script>

<style></style>
