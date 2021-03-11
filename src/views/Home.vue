<template>
  <div class="home">
    <div class="row">
      <MainPage
        v-for="(item, index) in animeList.anime"
        :key="index"
        :Name="item.title"
        :img="item.image_url"
        :id="item.mal_id"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import MainPage from "@/components/MainPage.vue";

export default {
  name: "Home",
  components: {
    MainPage,
  },
  props: {
    page: Number,
  },
  data() {
    return {
      animeList: null,
      url: "https://api.jikan.moe/v3/producer/1/1",
    };
  },
  mounted() {
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
