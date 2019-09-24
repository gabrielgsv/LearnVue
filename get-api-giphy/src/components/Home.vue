<template>
  <div v-if="gifs" class="container">
    <div v-for="gif in gifs" :key="gif.id">
      <img :src="gif.images.original.url" class="image" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      apiUrl: "http://api.giphy.com/v1/gifs",
      apiKey: "fJQVg190rqx0hoyn39QJKntmhmuw47Cs",
      gifs: null
    };
  },
  methods: {
    getGifs: function() {
      const url = `${this.apiUrl}/trending?api_key=${this.apiKey}`;

      axios.get(url).then(res => (this.gifs = res.data.data));
    }
  },
  created: function() {
    this.getGifs();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 100%;
  background-color: black;
  display: flex;
  flex-wrap: wrap;
}
.image {
  width: 300px;
  height: 300px;
  object-fit: cover;
}
</style>
