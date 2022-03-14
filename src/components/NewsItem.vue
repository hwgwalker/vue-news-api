<template>
  <div class="hello">
    <h1>Latest News</h1>
    <div v-for="item of items" :key="item.id">
      {{ item.title }}
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";

Vue.use(axios);

export default {
  name: "NewsItem",
  data() {
    return {
      items: [],
    };
  },
  async created() {
    try {
      const response = await axios.get(
        "https://niftyapi.madeatsilverchip.com/NewsArticles"
      );
      console.log(response);
      this.items = response.data;
    } catch (e) {
      console.log(e);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
