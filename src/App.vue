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
    <div class="small">
      <chart-test :chart-data="data" :options="options"></chart-test>
      <button @click="fillData()">Randomize</button>
    </div>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld";
import ChartTest from "@/ChartTest";
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
      dataCollection: null,
      data: {
        labels: [
          "가",
          "나",
          "다",
          "라",
          "마",
          "바",
          "사",
          "아",
          "자",
          "차",
          "카",
          "타",
          "파",
          "하",
        ],
        datasets: [
          {
            label: "테스트 데이터셋",
            data: [10, 3, 30, 23, 10, 5, 15, 25, 2, 4, 1, 13, 52, 23],
            borderColor: "rgba(255, 201, 14, 1)",
            backgroundColor: "rgba(255, 201, 14, 0.5)",
            fill: false,
          },
        ],
      },
      options: {
        responsive: true,
        title: {
          display: true,
          text: "막대 차트 테스트",
        },
        tooltips: {
          mode: "index",
          intersect: false,
        },
        hover: {
          mode: "nearest",
          intersect: true,
        },
        scales: {
          xAxes: [
            {
              display: true,
              scaleLabel: {
                display: true,
                labelString: "x축",
              },
            },
          ],
          yAxes: [
            {
              display: true,
              ticks: {
                autoSkip: false,
              },
              scaleLabel: {
                display: true,
                labelString: "y축",
              },
            },
          ],
        },
      },
    };
  },
  created() {
    this.fillData();
  },
  methods: {
    increase(product) {
      product.like += 1;
    },
    fillData() {
      this.dataCollection = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: "Main One",
            backgroundColor: "red",
            data: [this.getRandomInt(), this.getRandomInt()],
          },
          {
            label: "Main Two",
            backgroundColor: "blue",
            data: [this.getRandomInt(), this.getRandomInt()],
          },
        ],
      };
      console.log("ChartTestMain", this.dataCollection);
    },
    getRandomInt() {
      return Math.floor(Math.random() * (50 - 4)) + 5;
    },
  },
  components: {
    HelloWorld,
    ChartTest,
  },
};
</script>
.small { max-width: 600px; margin: 150px auto; }
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
