<template>

  <div class="black-bg" v-if="모달창 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>{{ contents }}</p>
      <button @click="모달창 = false">X</button>
    </div>
  </div>

  <dir class="menu">
    <a v-for="(a,j) in 메뉴들" :key="j"> {{ a }}</a>

  </dir>
  원룸샵
  <div v-for="(data,i) in 원룸들" :key="i">
    <img :src="data.image">
    <h4 @click="content(i)">{{ data.title }}</h4>
    <p>{{ data.price }} 만원</p>
    <button @click="addNum(i)">허위매물신고</button> <span>신고수: {{ 신고수[i] }}</span>
  </div>

</template>

<script>

import datas from './assets/oneroom.js';


export default {
  name: 'App',
  data: function(){
    return {
      이미지: [{fileUrl: require('./assets/room0.jpg')}, {fileUrl: require('./assets/room1.jpg')}, {fileUrl: require('./assets/room2.jpg')}],
      신고수: [0,0,0],
      prices: [60,70,80],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      메뉴들: ['Home', 'Shop', 'About'],
      모달창: false,
      원룸들: datas,
      contents: "",
    }
  },
  methods: { 
    addNum(i) {
      this.신고수[i] += 1;
    },
    content(i) {
      this.contents = this.원룸들[i].content;
      this.모달창 = true; 
    }
  }
}
</script>

<style>

body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
</style>
