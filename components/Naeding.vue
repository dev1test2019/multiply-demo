<template>
  <div>
    <v-card>
      <v-flex v-for="(item, index) in Naeding" :key="index" class="main-card">
        <div class="card-header">
          <div class="user-info">
            <img :src="base_url + item.user.profile_image_url" alt="">
            <div class="name">{{ item?.user.name }}</div>
            <div class="time">{{ $moment(item?.user.created_at).format("YYYY.M.D") }}</div>
          </div>
          <b-icon icon="bookmark"></b-icon>
        </div>
        <div class="card-body">
          <div class="content">{{ item.body }}</div>
          <div class="image-container" v-if="item.image_count > 0">
            <img v-for="(image, img_index) in item.images" :key="img_index" :src="base_url + image.image_url" alt="">
          </div>
        </div>
      </v-flex>
      <v-card v-intersect="infiniteScrolling"></v-card>
    </v-card>
    <div v-if="is_loading" class="loading-icon">
      <b-icon icon="arrow-clockwise" animation="spin-pulse" font-scale="4"></b-icon>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Naeding",
  data() {
    return {
      base_url: "http://naeding.com:444",
      FetchData: [],
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
    },
    infiniteScrolling(entries, observer, isIntersecting) {
      this.is_loading = true
      this.page++;
      axios
        .get(this.url)
        .then(response => {
          let result = response.data.page.data
          result.forEach(item => this.Naeding.push(item));
          this.is_loading = false
        })
        .catch(err => {
          console.log(err);
          this.is_loading = false
        });
    }
  }
};
</script>

<style scoped>
.theme--light.v-card {
  background-color: #f5f5f5;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.card-header .bi-bookmark {
  cursor: pointer;
}

.user-info {
  display: flex;
  align-items: center;
}

.user-info img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.user-info .name {
  margin: 0 8px;
  font-size: 16px;
  font-weight: 600;
}

.image-container img {
  width: 100%;
}

.loading-icon {
  display: flex;
  justify-content: center;
  margin: 20px 0;
}
</style>
