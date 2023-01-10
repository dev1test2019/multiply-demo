<template>
  <v-card>
    <v-flex v-for="(item, index) in Naeding" :key="index" class="main-card">
      <div class="card-header">
        <div class="user-info">
          <img :src="item.user.profile_image_url" alt="">
          <div class="name">{{ item?.user.name }}</div>
          <div class="time">{{ item?.user.created_at }}</div>
        </div>
        <div class="bookmark"></div>
      </div>
      <div class="card-body">
        <div class="content">{{ item.body }}</div>
        <div class="image-container" v-if="item.image_count > 0">
          <img v-for="(image, img_index) in item.images" :key="img_index" :src="image.image_url" alt="">

        </div>
      </div>

    </v-flex>
    <!--Add here the vuetify directive -->
    <v-card v-intersect="infiniteScrolling"></v-card>
  </v-card>
</template>

<script>
import axios from "axios";

export default {
  name: "Naeding",
  data() {
    return {
      Naeding: [],
      page: 0
    };
  },
  computed: {
    url() {
      return "http://naeding.com:444/api/story?page=" + this.page;
    }
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const response = await axios.get(this.url);
      this.Naeding = response.data.page.data;
    },
    infiniteScrolling(entries, observer, isIntersecting) {
      setTimeout(() => {
        this.page++;
        axios
          .get(this.url)
          .then(response => {
            let result = response.data.page.data
            result.forEach(item => this.Naeding.push(item));
            console.log(response);
          })
          .catch(err => {
            console.log(err);
          });
      }, 500);
    }
  }
};
</script>

<style scoped>
.theme--light.v-card {
  background-color: #f5f5f5;
}
</style>
