<template>
  <div>
    <router-link :to="`/anime/${this.id}`" class="col-3">
      <b-card
        border-variant="info"
        :header="Name"
        alin="center"
        style="height: 30rem"
      >
        <b-card-text>
          <b-img :src="img" fluid alt="Fluid image"> </b-img>
        </b-card-text>
      </b-card>
    </router-link>
  </div>
</template>
<script>
export default {
  props: {
    id: Number,
    index: Number,
    name: String,
    img: String,
  },
};
</script>
