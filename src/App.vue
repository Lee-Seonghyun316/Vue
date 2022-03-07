<template>
  <div id="app">
    <div class="menu">
      <a href="" v-for="(menu, i) in menus" :key="menu">{{ i }}{{ menu }}</a>
    </div>

    <img alt="Vue logo" src="./assets/logo.png" />
    <div v-for="product in productsObj" :key="product.id">
      <h4 class="red" :style="style1">{{ product.name }}</h4>
      <p>{{ product.price }}만원</p>
      <p v-if="product.count === 0">품절</p>
      <button v-on:click="increase(product)">좋아요</button
      ><span>좋아요수 : {{ product.like }}</span>
      <!--<button @click="">싫어요</button>-->
    </div>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld";
import { products } from "@/data/products";

export default {
  name: "App",
  data() {
    return {
      좋아요수: 0,
      price1: 60,
      price2: 70,
      style1: "color: blue;",
      products: ["꽃무늬원피스", "고급원피스", "정장원피스"],
      menus: ["Home", "Products", "About"],
      productsObj: [
        { id: 1, name: "꽃무늬원피스", price: 60, like: 0, count: 0 },
        { id: 2, name: "고급원피스", price: 70, like: 1, count: 1 },
        { id: 3, name: "정장원피스", price: 80, like: 2, count: 1 },
      ],
      productsData: products,
    };
  },
  methods: {
    increase(product) {
      product.like += 1;
    },
  },

  components: {
    HelloWorld,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}
</style>
