<template>
  <div class="menu">
    <a v-for="(menu,i) in menus" :key="i" href>{{ menu }}</a>
  </div>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>

  <div v-for="(item,i) in items" :key="i">
    <img :src="item.image" class="room-img" />
    <h4 @click="openModal">{{ item.product }}</h4>
    <p>{{ item.price }}</p>
    <button @click="increase(i)">허위매물신고</button>
    <button @click="decrease(i)">허위매물신고 취소</button>
    <span>신고수 : {{ item.신고수 }}</span>
  </div>

  <div v-for="(item,i) in 원룸데이터" :key="i">
    <img :src="item.image" class="room-img" />
    <h4 @click="openModal">{{ item.title }}</h4>
    <p>{{ item.price }}</p>
    <p>{{ item.content }}</p>
  </div>
</template>

<script>
import oneroomData from "./assets/oneroom";

export default {
  name: "App",
  data() {
    return {
      원룸데이터: oneroomData,
      items: [
        {
          product: "역삼동원룸",
          price: 50,
          신고수: 0,
          image: require("./assets/room0.jpg")
        },
        {
          product: "천호동원룸",
          price: 70,
          신고수: 0,
          image: require("./assets/room1.jpg")
        },
        {
          product: "마포구원룸",
          price: 90,
          신고수: 0,
          image: require("./assets/room2.jpg")
        }
      ],
      menus: ["Home", "Shop", "About"],
      모달창열렸니: false
    };
  },
  methods: {
    increase(index) {
      this.items[index].신고수++;
    },
    decrease(index) {
      this.items[index].신고수--;
    },
    openModal() {
      this.모달창열렸니 = true;
    },
    closeModal() {
      this.모달창열렸니 = false;
    }
  },
  components: {}
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
