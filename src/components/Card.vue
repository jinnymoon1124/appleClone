<template>
  <div> <!--메인화면내용-->
    <img :src="data.image" class="areaimg">
    <h4 @click="$emit('openModal', data.id)">{{ data.title }}</h4>
    <p>주요 관광지 : {{ data.content }}</p>
    <p>가격 : {{ data.price }}원</p>
    
    <button @click="$emit('voteNum')">♥</button> 
    <span> 가고싶어요 : {{ vote }}</span>
  </div>
</template>

<script>
export default {
    name : "Card",
    props : {
      data : Array,
      vote : Number,
    }
}
</script>

<style>
  .areaimg {
    width: 500px;
    margin-top: 40px;
  }
</style>