<template>
  <main>
    <h1>Our Taco Friends:</h1>
    <ul>
      <li v-for="friend in friends" :key="friend" @click="clickFriend(friend)">
        {{ friend }}
      </li>
    </ul>
    <p><i>Click on a friend!</i></p>
  </main>
</template>

<script>
import { reactive, toRefs } from "@vue/composition-api";

export default {
  setup() {
    const state = reactive({
      friends: [
        "Sarah likes all tacos",
        "Brian Holt likes whiskey more than tacos",
        "Shirley Wu likes tacos as much as Wonder Woman"
      ]
    });

    function clickFriend(friend) {
      alert(friend);
    }

    return {
      ...toRefs(state),
      clickFriend
    };
  }
};
</script>

<style lang="scss" scoped>
ul {
  width: 400px;
}
li {
  text-align: left;
  transition: all 0.4s ease;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
i {
  color: #555;
}
</style>
