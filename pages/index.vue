<template>
  <v-container class="main-app">
    <!-- header  -->
    <div class="header">
      <v-container fluid grid-list-lg>
        <div class="logo">내딩</div>
        <b-input-group size="sm" class="search-bar">
          <b-input-group-prepend is-text>
            <b-icon icon="search"></b-icon>
          </b-input-group-prepend>
          <b-form-input type="search" placeholder="Search terms"></b-form-input>
        </b-input-group>
      </v-container>
    </div>

    <!-- body  -->
    <v-container fluid grid-list-lg class="body">
      <Naeding />
    </v-container>

    <!-- footer  -->
    <div class="footer">
      <v-container fluid grid-list-lg>
        <div class="footer-icon">
          <b-icon icon="menu-up"></b-icon>
          <p>menu</p>
        </div>
        <div class="footer-icon">
          <b-icon icon="shield-fill-check"></b-icon>
          <p>location</p>
        </div>
        <div class="footer-icon">
          <b-icon icon="house"></b-icon>
          <p>home</p>
        </div>
        <div class="footer-icon">
          <b-icon icon="menu-button-wide-fill"></b-icon>
          <p>note</p>
        </div>
        <div class="footer-icon">
          <b-icon icon="person-fill"></b-icon>
          <p>MY</p>
        </div>
      </v-container>
      <div class="btn-create">
        <b-icon icon="pencil"></b-icon>
      </div>
    </div>

  </v-container>
</template>

<script>
import Naeding from "~/components/Naeding.vue";
import "@/assets/css/layout.css";

export default {
  components: { Naeding }
};
</script>