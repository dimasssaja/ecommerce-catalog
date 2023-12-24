<template>
  <div class="container-unavailable">
    <div class="main-unavailable">
      <p class="desc-unavailable">This product is unavailable to show</p>
      <button class="button-unavailable" @click="increment">
        Next Product
      </button>
      <div class="image-background">
        <img class="face-sad" src="../assets/Sad-Face.svg" :alt="altText" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardUnavailable",
  data() {
    return {
      altText: "Sad Face image",
    };
  },
  props: ["increment"],
};
</script>

<style scoped>
@import "../assets/style/CardUnavailable.css";
</style>
