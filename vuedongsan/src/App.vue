<template>

  <div class="balck-bg" v-if="modal">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>내용</p>
      <button @click="modal = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menu" :key="i">{{ menu }}</a>
  </div>

  <!-- 
    {{ 데이터 바인딩 }} 하는 이유
    1. 변경하기 쉽게 하기 위해 -> 자주 변경될 데이터들
    2. 실시간 렌더링 기능
  -->
  <!-- <div>
    <h4 :style="textColor">{{products[0]}}</h4>
    <p>{{ price1 }}만원</p>
  </div>

  <div>
    <h4>XX 원룸</h4>
    <p>{{ price2 }}</p>
  </div> -->

  <div>
    <div v-for="(product, i) in products" :key="i" class="container">
      <img :src="product.image" alt="room" class="room-img">
      <h4 @click="modal = true">{{ product.room }}</h4>
      <p>{{ product.price }} 만원</p>
      <button @click="increase($event)" :data-id="i">허위매물신고</button>
      <p>신고수: {{ report[i] }}</p>
    </div>
  </div>
</template>

<script>

import oneRoomData from './data/oneRoom.js';


export default {
  name: 'App',

  data() {
    return {
      menu: ['Home', 'Shop', 'About'],
      report: [0, 0, 0],
      // products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      // price: ['50만원', '60만원', '70만원'],
      products: [
        {
          room: '역삼동원룸',
          price: 50,
          image: require('./assets/room0.jpg'),
        },
        {
          room: '천호동원룸',
          price: 60,
          image: require('./assets/room1.jpg'),
        },
        {
          room: '마포구원룸',
          price: 70,
          image: require('./assets/room2.jpg'),
        },
      ],
      modal: false,
      oneRoomData: oneRoomData,
    }
  },

  components: {},
  methods: {
    // 함수안에서 데이터를 사용하고 싶을 때는 this.데이터명 형식으로 사용해야한다.
    increase(event) {
      const current = event.target.dataset.id

      for (let i = 0; i < this.report.length; i++) {
        parseInt(current) === i ? this.report[i]++ : null
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.balck-bg {
  position: fixed;
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,.5);
}

.balck-bg .white-bg {
  position: absolute;
  width: 500px;
  margin: auto;
  top: 50%;
  left: 50%;
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  transform: translate(-50%, -50%);
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: #fff;
  padding: 10px;
  text-decoration: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.container .room-img {
  width: 50vw;
  margin-top: 5vw;
}
</style>
