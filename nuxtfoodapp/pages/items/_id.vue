<template>
  <main class="container">
    <section
      class="image"
      :style="{
        background: `rgba(0, 0, 0, 0) url(${itemImage}) no-repeat scroll center center;`
      }"
    ></section>
    <section class="details">
      <h2>{{ currentItem.item }}</h2>
      <h3>Price: ${{ currentItem.price }}</h3>
      <div class="quantity">
        <input v-model="itemCount" type="number" min="1" />
        <button class="primary">Add to Cart ${{ totalPrice }}</button>
      </div>
      <fieldset>
        <legend><h3>Add Ons</h3></legend>
        <div v-for="addOn in currentItem.addOns" :key="addOn">
          <input
            @change="e => (selectedAddOn = e.target.value)"
            :id="addOn"
            type="checkbox"
            name="addon"
            :value="addOn"
            :checked="addOn === selectedAddOn ? 'true' : ''"
          />
          <label :for="addOn">{{ addOn }} </label>
        </div>
      </fieldset>
    </section>
    <section class="options">
      <h3>Description</h3>
      <p>{{ currentItem.description }}</p>
    </section>
  </main>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      id: this.$route.params.id,
      itemCount: 1,
      selectedAddOn: ""
    };
  },
  computed: {
    ...mapState(["foodData"]),
    currentItem() {
      let result;

      for (let i = 0; i < this.foodData.length; i++) {
        for (let j = 0; j < this.foodData[i].menu.length; j++) {
          if (this.foodData[i].menu[j].id === this.id) {
            result = this.foodData[i].menu[j];
            break;
          }
        }
      }

      return result;
    },
    itemImage() {
      return "/" + this.currentItem.img;
    },
    totalPrice() {
      return Number(this.currentItem.price * this.itemCount).toFixed(2);
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  width: 1000px;
  margin: 100px auto;
  display: grid;
  grid-template-columns: 400px 1fr;
  grid-template-rows: 400px 1fr;
  grid-column-gap: 60px;
  grid-row-gap: 60px;
  line-height: 2;
}

.image {
  grid-area: 1 / 1 / 2 / 2;
}
.details {
  grid-area: 1 / 2 / 2 / 3;
  position: relative;
}
.options {
  grid-area: 2 / 1 / 3 / 2;
}
.quantity {
  display: flex;
  margin: 20px 0 40px;
}
fieldset {
  margin: 20px 0;
  border: 1px solid #ddd;
}
</style>
