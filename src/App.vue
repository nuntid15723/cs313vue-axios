<template>
  <div id="app">
    <b-navbar type="dark" variant="dark">
      <b-navbar-nav id="nav">
        <router-link to="/">Home</router-link> 
      </b-navbar-nav>
      <b-nav-form class="offset-md-10">
        <b-nav-input
          size="sm"
          class="mr-sm-2 col-8"
          placeholder="Search"
          v-model="sh"
        ></b-nav-input>
        <b-button size="sm" class="my-2-my-sm-0" type="submit" @click="Search()"
          >Search</b-button
        >
      </b-nav-form>
    </b-navbar>
    <router-view/>
   
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      sh: "",
      animeList: null,
      url: "",
    };
  },
  methods: {
    Search() {
      const router = this.$router;
      for (let i = 0; i <= this.animeList.anime.length; i++) {
        if (this.sh == this.animeList.anime[i].title) {
          alert(this.animeList.anime[i].title);
          router.push({
            path: `/anime/${this.animeList.anime[i].mal_id}`,
          });
          break;
        } else if (99 == i) {
          router.push({
            path: `/`,
          });
        }
      }
    },
  },
  mounted() {
    this.url = "https://api.jikan.moe/v3/producer/1/1";
    axios
      .get(this.url)
      .then((result) => {
        this.animeList = result.data;
      })
      .catch((err) => {
        console.log(err);
        alert(err);
      });
  },
};
</script>

<style>

</style>
