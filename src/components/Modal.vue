<template>
   <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <p>{{원룸들[누른거].price}}원</p>
      <p><img :src="원룸들[누른거].image" style="width:500px;" alt=""></p>
      <input type="number"><br>
      <a href="#none"  @click="$emit('closemodal')" style="display:inline-block;text-align:right;font-weight:bold" >닫기</a>
    </div>
  </div>
</template>

<script>
export default {
  name : 'ModalPop',
  props : {
    원룸들 : Array,
    누른거 : Number,
    모달창열렸니 : Boolean,
  }
}
</script>

<style>
  
</style>