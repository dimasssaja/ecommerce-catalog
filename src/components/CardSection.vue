<template>
  <div class="container">
    <div class="main">
      <div class="image">
        <img :src="product.image" :alt="product.category" />
      </div>
      <div class="description">
        <h4
          :class="[
            product.category == 'men\'s clothing' ? 'color-men' : 'color-women',
          ]"
        >
          {{ product.title }}
        </h4>
        <div class="product-rate">
          <p class="product-category">{{ product.category }}</p>
          <div
            :class="[
              product.category == 'men\'s clothing'
                ? 'color-rate-men'
                : 'color-rate-women',
            ]"
          >
            <p class="rate">{{ product.rating.rate }}/5</p>
            <div
              :class="[
                Math.round(product.rating.rate) > 0
                  ? 'circle bg-color'
                  : 'circle',
              ]"
            ></div>
            <div
              :class="[
                Math.round(product.rating.rate) > 1
                  ? 'circle bg-color'
                  : 'circle',
              ]"
            ></div>
            <div
              :class="[
                Math.round(product.rating.rate) > 2
                  ? 'circle bg-color'
                  : 'circle',
              ]"
            ></div>
            <div
              :class="[
                Math.round(product.rating.rate) > 3
                  ? 'circle bg-color'
                  : 'circle',
              ]"
            ></div>
            <div
              :class="[
                Math.round(product.rating.rate) > 4
                  ? 'circle bg-color'
                  : 'circle',
              ]"
            ></div>
          </div>
        </div>

        <hr />
        <p class="desk">{{ product.description }}</p>
        <hr />
        <h4
          :class="[
            product.category == 'men\'s clothing' ? 'color-men' : 'color-women',
          ]"
        >
          ${{ product.price }}
        </h4>
        <div class="button-group">
          <button
            :class="[
              product.category == 'men\'s clothing'
                ? 'buy-clr-men'
                : 'buy-clr-women',
            ]"
          >
            Buy now
          </button>
          <button
            :class="[
              product.category == 'men\'s clothing'
                ? 'next-clr-men'
                : 'next-clr-women',
            ]"
            @click="increment"
          >
            Next Product
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardSection",
  props: ["product", "increment"],
};
</script>
<style scoped>
@import "../assets/style/CardSection.css";
</style>
