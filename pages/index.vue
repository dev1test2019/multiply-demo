<template>
  <div>
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

    </div>
  </div>
</template>

<script>
import Naeding from "~/components/Naeding.vue";

export default {
  components: { Naeding }
};
</script>

<style scoped>
.header,
.footer {
  position: fixed;
  box-shadow: 0px 0px 1px 1px #d2d2d2;
}

.header {
  top: 0;
  z-index: 2;
  background: white;
  width: 100%;
}

.body {
  margin: 46px 0;
}

.footer {
  bottom: 0;
  width: 100%;
  background: white;
  height: 65px;
}

.footer .container {
  display: flex;
  justify-content: space-between;
}

.footer .footer-icon {
  text-align: center;
  width: 20%;
}

.search-bar {
  width: calc(100% - 60px);
}

.header .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header .logo {
  color: #ffcc03;
  font-weight: 700;
  font-size: 26px;
}

.search-bar input.form-control,
.search-bar .input-group-text {
  background-color: #f5f5f5;
  border-color: #f5f5f5;
  color: #b1b1b5;
}

.search-bar input.form-control {
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;
}

.search-bar .input-group-text {
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
}
</style>
