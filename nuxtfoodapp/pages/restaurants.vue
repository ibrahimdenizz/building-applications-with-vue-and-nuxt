<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <app-select @change="selectedRestaurant = $event" />
      <pre>{{ $data }}</pre>
    </div>
    <app-restaurant-info />
  </main>
</template>

<script>
export default {
  data() {
    return {
      selectedRestaurant: ""
    };
  }
};
</script>

<style lang="scss" scoped></style>
