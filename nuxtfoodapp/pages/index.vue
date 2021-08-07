<template>
  <main class="container">
    <app-header />
    <app-restaurant-info :data-source="foodData" />
  </main>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["foodData"])
  }
};
</script>
