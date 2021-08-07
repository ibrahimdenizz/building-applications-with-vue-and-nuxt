<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <app-select @change="selectedRestaurant = $event" />
    </div>
    <app-restaurant-info :data-source="filteredRestaurants" />
  </main>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      selectedRestaurant: ""
    };
  },
  computed: {
    ...mapState(["foodData"]),
    filteredRestaurants() {
      if (this.selectedRestaurant) {
        return this.foodData.filter(el => {
          let name = el.name.toLowerCase();
          return name.includes(this.selectedRestaurant);
        });
      } else return this.foodData;
    }
  }
};
</script>

<style lang="scss" scoped></style>
