<template>
  <div>
    <!-- header  -->
    <div class="header">
      <v-container fluid grid-list-lg>
        <b-input-group size="sm" class="mb-2">
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
}

.header {
  top: 0;
  z-index: 2;
  background: white;
  width: 100%;
  height: 65px;
}

.body {
  margin: 70px 0;
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
  padding: 0 5%;
}
</style>
