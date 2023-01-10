<template>
  <v-container fluid grid-list-lg class="mt-5">
    <b-input-group size="sm" class="mb-2">
      <b-input-group-prepend is-text>
        <b-icon icon="search"></b-icon>
      </b-input-group-prepend>
      <b-form-input type="search" placeholder="Search terms"></b-form-input>
    </b-input-group>
    <Naeding />
  </v-container>
</template>

<script>
import Naeding from "~/components/Naeding.vue";


export default {
  components: { Naeding }
};

</script>
