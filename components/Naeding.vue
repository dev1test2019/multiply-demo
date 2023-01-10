<template>
  <div>
    <v-flex v-for="(item, index) in Naeding" :key="index" class="main-card">
      <v-card>
        <div class="card-header">
          <div class="user-info">
            <img :src="base_url + item.user.profile_image_url" alt="avatar" v-lazy-load>
            <div class="name">{{ item?.user.name }}</div>
            <div class="time">{{ $moment(item?.user.created_at).format("YYYY.M.D") }}</div>
          </div>
          <b-icon icon="bookmark"></b-icon>
        </div>
        <div class="card-body">
          <div class="content-title">{{ item.title }}</div>
          <div class="content-body">{{ item.body }}</div>
          <div class="image-container" v-if="item.image_count > 0">
            <img v-for="(image, img_index) in item.images" :key="img_index" :src="base_url + image.image_url"
              v-lazy-load>
          </div>
        </div>
        <div class="card-footer">
          <b-icon icon="heart"></b-icon>
          <div class="like">Like <span>{{ item.likes_count }}</span></div>
          <div class="comment">Comment <span>{{ item.comments_count }}</span></div>
        </div>
      </v-card>
    </v-flex>
    <v-card v-intersect="infiniteScrolling"></v-card>
    <div v-if="is_loading" class="loading-icon">
      <b-icon icon="arrow-clockwise" animation="spin-pulse" font-scale="4"></b-icon>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import "@/assets/css/naeding.css";

export default {
  name: "Naeding",
  data() {
    return {
      base_url: "http://naeding.com:444",
      Naeding: [],
      page: 1,
      is_loading: true
    };
  },
  computed: {
    url() {
      return this.base_url + "/api/story?page=" + this.page;
    }
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const response = await axios.get(this.url);
      this.Naeding = response.data.page.data;
      this.is_loading = false
      this.page++;
    },
    infiniteScrolling(entries, observer, isIntersecting) {
      if (isIntersecting && this.page > 1) {
        this.is_loading = true
        axios
          .get(this.url)
          .then(response => {
            let result = response.data.page.data
            result.forEach(item => this.Naeding.push(item));
            this.is_loading = false
            this.page++;
          })
          .catch(err => {
            console.log(err);
            this.is_loading = false
          });
      }
    }
  }
};
</script>