<template>
  <div>
    <div v-if="gifs">
      <p>chegou aqui</p>
    </div>
    <div v-for="gif in gifs" :key="gif.id">
      <img :src="gif.images.original.url" />
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

      axios.get(url).then(res => (this.gifs = res.data));
    }
  },
  created: function() {
    this.getGifs();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
