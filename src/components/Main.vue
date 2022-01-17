<template>
  <main>
    <div class="album-container">
      <Album
        v-for="(album, index) in albums"
        :key="index"
        :src="album.poster"
        :title="album.title"
        :author="album.author"
        :year="album.year"
      />
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";
export default {
  components: {
    Album,
  },
  data() {
    return {
      albums: null,
    };
  },
  created() {
    this.getArrayApi();
  },
  methods: {
    getArrayApi: function () {
      // Make a request for a user with a given ID
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.albums = response.data.response;
          console.log(this.albums);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "../assets/scss/partials/variables.scss";
main {
  padding-top: 4.7em;
  background-color: $mainBc;
  .album-container {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    width: 70%;
    .album-box {
      flex-basis: calc((100% / 5) - 2em);
      background-color: #2e3a46;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 1em;
      padding: 2em 0 0 0;
      .album-cover {
        width: 150px;
        img {
          width: 100%;
        }
      }
      .album-details {
        text-align: center;
        padding: 1em;
        h2 {
          margin-bottom: 1em;
          text-transform: uppercase;
          color: white;
        }
        h3,
        h4 {
          color: grey;
          font-size: 0.9em;
        }
      }
    }
  }
}
</style>
