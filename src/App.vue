<template>

<!-- <div v-if="1 == 2">
  안녕하세요
</div>
<div v-else-of="1 == 1">
  안녕하세요2
</div> -->


<!-- <div class="start" :class="{ end : 모달창열렸니 }"> -->
<transition name="fade">
  <!-- 모달창 -->
  <ModalPop @closemodal="모달창열렸니 = false;" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />
  <!-- //모달창 -->
</transition>
 <!-- </div> -->

  <OpenBanner />
  <Discount />


  <div class="menu">
    <a href="" v-for="(m,i) in 메뉴들" :key="m">{{메뉴들[i]}}</a>
  </div>

  
  <Card @openmodal="모달창열렸니 = true; 누른거 = i" :원룸="원룸들[i]" v-for="(원룸,i) in 원룸들" :key="원룸" />

  <!-- <div class="pro-wrap" v-for="(p,i) in 원룸들" :key="p">
    <img src="./assets/cont01.png" alt="">
    <h4 @click="모달창열렸니 = true; 누른거 = i">{{원룸들[i].title}}</h4>
    <p>{{원룸들[i].price}}$</p>
    <button @click="신고수[i] += 1">허위매물 신고하기</button> <span>{{신고수[i]}}</span>
  </div> -->

   <!-- <button @click="increase">허위매물 신고하기</button> <span>{{신고수1}}</span>

  <div>
    <img :src="원룸들[0].image" alt="">
    <h4>{{원룸들[0].title}}</h4>
    <p>{{원룸들[0].price}}</p>
  </div> -->
</template>

<script>
import oneloomList from './assets/oneroom.js'
import Discount from './components/Discount.vue'
import OpenBanner from './components/Banner'
import ModalPop from './components/Modal.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  data(){
    return{
      오브젝트 : {이름 : 'kim', age : 20},
      누른거 : 0,
      원룸들 : oneloomList,
      모달창열렸니 : false,
      신고수1 : 0,
      // 신고수 : [0,0,0],
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
    Discount: Discount,
    OpenBanner : OpenBanner,
    ModalPop : ModalPop,
    Card : Card
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

.start {
  opacity: 0;
  transition:all ease 1s;
}
.end {
  opacity: 1;
}

.fade-enter-from {opacity: 0;}
.fade-enter-active {transition:all ease 1s}
.fade-enter-to {opacity: 1;}
.fade-leave-from {opacity: 1;}
.fade-leave-active {transition:all ease 1s}
.fade-leave-to {opacity:0;}
</style>
