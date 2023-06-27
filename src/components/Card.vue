<template>  
  <div class="pro-wrap">
    <img :src="원룸.image" alt="" style="width:500px;">
    <h4 @click="send">{{원룸.title}}</h4>
    <p>{{원룸.price}}$</p>
  </div>
</template>

<script>
export default {
  name : 'CardList',
  props : {
    원룸 : Object,
  },
  methods: {
    send(){
      this.$emit('openmodal',this.원룸.id)
    }
  },
}
</script>

<style>
  
</style>