<template>
   <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <p><img :src="원룸들[누른거].image" style="width:500px;" alt=""></p>
      <!-- <input @input="month = $event.target.value"><br> -->
      <input v-model="month"><br>
      <!-- <input v-model="month"> -->
      <!-- <select v-model="month">
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
      </select> -->
      <!-- <input type="checkbox" v-model="month" /> -->
      <!-- <input type="range" min="1" max="12" v-model="month" > -->
      <p>{{ month }}개월 선택함 : {{원룸들[누른거].price * month}}원</p>
      <a href="#none" @click="$emit('closemodal')" style="display:inline-block;text-align:right;font-weight:bold" >닫기</a>
    </div>
  </div>
</template>

<script>
export default {
  name : 'ModalPop',
  data(){
    return{
    month : 1,
    }
  },
  watch : {
    month(a){
      if (a > 13){
        alert('13보다 작은 개월수를 입력해주세요')
      }
      if(isNaN(a) == true){
        alert('숫자만 입력')
        // a = 1;
        this.month = 1;
      }
    }
  },
  beforeUpdate() {
    if(this.month == 2){
      alert('2개월은 불가능합니다.')
      this.month = 3
    }
  },
  props : {
    원룸들 : Array,
    누른거 : Number,
    모달창열렸니 : Boolean,
  },
}
</script>

<style>
  
</style>