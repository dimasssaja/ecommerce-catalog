
<template>
 
  <div>
    
    <div class="container-product-men">
      <div>
       
        <LoaderSection v-if="load" />
        
        <div v-else>
          <CardUnavailable
            v-if="category == 2"
            :product="products"
            :increment="increment"
          />
          <CardSection v-else :product="products" :increment="increment" />
        </div>
      </div>
    </div>
 
    <div class="bg-pattern-men" v-if="category == 0"></div>
    <div class="bg-pattern-women" v-else-if="category === 1"></div>
    <div class="bg-pattern-unavailable" v-else></div>
  </div>
</template>


<script>


import CardSection from "@/components/CardSection.vue";
import CardUnavailable from "@/components/CardUnavailable.vue";
import LoaderSection from "@/components/LoaderSection.vue";

import axios from "axios";

export default {

  name: "HomeView",

  components: {
    CardSection,
    CardUnavailable,
    LoaderSection,
  },
  data() {
    return {
      load: true,
      products: [],
      category: 0,
      number: 1,
    };
  },
  methods: {
    set(data) {
      this.products = data;
    },

    increment() {
      if (this.number >= 20) {
        this.number = 1;
      } else {
        this.number++;
        console.log("data", this.number);
      }
    },
  },

  mounted() {
    console.log("data", this.number);
    this.load = true;

    axios
      .get("https://fakestoreapi.com/products/" + this.number)
      .then((response) => {
        if (response.data.category == "men's clothing") {
          this.category = 0;
          console.log("men");
        } else if (response.data.category == "women's clothing") {
          this.category = 1;
          console.log("women");
        } else {
          this.category = 2;
          console.log("other");
        }
        console.log(response);
        this.set(response.data);
        this.load = false;
      })
      .catch((error) => console.log("Failed : ", error));
  },

  watch: {

    number() {
      if (this.load == false) {
        this.load = true;

        axios
          .get("https://fakestoreapi.com/products/" + this.number)
          .then((response) => {
            if (response.data.category == "men's clothing") {
              this.category = 0;
              console.log("men");
            } else if (response.data.category == "women's clothing") {
              this.category = 1;
              console.log("women");
            } else {
              this.category = 2;
              console.log("other");
            }
            this.set(response.data);
            this.load = false;
          })
          .catch((error) => console.log("Failed : ", error));
      }
    },
  },
};
</script>


<style>

@import "../assets/style/HomeView.css";
</style>
