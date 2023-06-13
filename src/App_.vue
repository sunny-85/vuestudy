<template>

<!-- <div v-if="1 == 2">
  안녕하세요
</div>
<div v-else-of="1 == 1">
  안녕하세요2
</div> -->
<!-- 모달창 -->

<div class="black-bg" v-if="모달창열렸니 == true" @click="모달창열렸니 = false">
  <div class="white-bg">
    <h4>{{원룸들[tit_num].title}}</h4>
    <p>{{원룸들[tit_num].content}}</p>
    <p>{{원룸들[tit_num].price}}원</p>
    <p><img :src="원룸들[tit_num].image" style="width:500px;" alt=""></p>
    <a href="#none" style="display:inline-block;text-align:right;font-weight:bold" @click="모달창열렸니 = false">닫기</a>
  </div>
</div>
<!-- //모달창 -->

<Discount />


  <div class="menu">
    <a href="" v-for="(m,i) in 메뉴들" :key="m">{{메뉴들[i]}}</a>
  </div>
  <div class="pro-wrap" v-for="(p,i) in 원룸들" :key="p">
    <img src="./assets/cont01.png" alt="">
    <h4 @click="모달창열렸니 = true; tit_num = i">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}$</p>
    <button @click="신고수[i] += 1">허위매물 신고하기</button> <span>{{신고수[i]}}</span>
  </div>

   <button @click="increase">허위매물 신고하기</button> <span>{{신고수1}}</span>

  <div>
    <img :src="원룸들[0].image" alt="">
    <h4>{{원룸들[0].title}}</h4>
    <p>{{원룸들[0].price}}</p>
  </div>
</template>

<script>
import oneloomList from './assets/oneroom.js'
import Discount from './components/Discount.vue'

export default {
  name: 'App',
  data(){
    return{
      tit_num : 0,
      원룸들 : oneloomList,
      모달창열렸니 : false,
      신고수1 : 0,
      신고수 : [0,0,0],
      메뉴들 : ['Home','Shop','About'],
      product : ['강남','대치','목동'],
      price : ['50','40','30'],
    }
  },
  methods: {
    increase(){
      this.신고수1 += 1
    }
  },
  components: {
    Discount
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
  margin-top: 30px;
}

div{
  box-sizing: border-box;
}

.black-bg {
  width :100%;height:100%;background:rgba(0,0,0,0.5);position:fixed;padding:20px;
}

.white-bg {
  width:100%;background:#fff;border-radius: 8px;padding:20px;
}

.menu {
  display: flex;
  justify-content: space-around;
  padding:10px;
  border-radius: 10px;
  background:#0336a8;
  margin:0 50px;
}
.menu a{
  flex: 1;
  color:#fff;
  font-weight: bold;
  font-size: 20px;
  text-decoration: none;
}

.discount {
  background:gray;
  margin:10px;
  padding:10px;
  border-radius: 5px;
}
</style>
