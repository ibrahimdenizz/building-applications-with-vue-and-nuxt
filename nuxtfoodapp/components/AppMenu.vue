<template>
  <nav>
    <ul>
      <li>
        <nuxt-link exact to="/"><app-logo /></nuxt-link>
      </li>
      <li>
        <nuxt-link to="/restaurants">
          Restaurants
        </nuxt-link>
      </li>
    </ul>
    <div v-if="totalCount" class="smallnum">{{ totalCount }}</div>
    <nuxt-link to="/cart">Cart</nuxt-link>
  </nav>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters(["totalCount"])
  }
};
</script>

<style lang="scss" scoped></style>
