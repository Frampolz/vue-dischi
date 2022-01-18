<template>
  <main>
    <Select @filterGnr="genrefilter($event)" />
    <div class="album-container" v-if="filtered">
      <Album
        v-for="(album, index) in filtered"
        :key="index"
        :src="album.poster"
        :title="album.title"
        :author="album.author"
        :year="album.year"
      />
    </div>
    <Album />
    <Loader v-if="!albums" />
  </main>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";
import Loader from "./Loader.vue";
import Select from "./Select.vue";

export default {
  components: {
    Album,
    Loader,
    Select,
  },
  data() {
    return {
      albums: null,
      filtered: null,
      selectValue: "",
    };
  },
  created() {
    this.getArrayApi();
  },

  methods: {
    getArrayApi: function () {
      setTimeout(() => {
        axios
          .get("https://flynn.boolean.careers/exercises/api/array/music")
          .then((response) => {
            this.albums = response.data.response;
            this.filtered = response.data.response;
            console.log(this.albums);
          })
          .catch(function (error) {
            console.log(error);
          });
      }, 2000);
    },
    genrefilter(value) {
      this.selectValue = value;
      if (this.selectValue == "") {
        this.filtered = this.albums;
        //console.log("qui");
      } else {
        return (this.filtered = this.albums.filter((element) =>
          element.genre.toLowerCase().includes(this.selectValue)
        ));
      }
    },
  },
};
</script>

<style lang="scss">
@import "../assets/scss/partials/variables.scss";
main {
  padding-top: 3.6em;
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
