<template>
  <div class="mi_con">
    <div v-for="(item,index) of music" :key="index">
      <div class="item">
        <div class="music_info_con">
          <img class="item_cover" src="@/assets/images/newyear.jpg">
          <div class="music_info">
            <span class="mo_name">{{item.title}}</span>
            <span class="mo_singer">{{item.singer}}</span>
          </div>
        </div>
        <img
          class="mo_play"
          :src=" item.isPlayed? require('@/assets/images/v2/pause.png'): require('@/assets/images/v2/play.png')"
          @click="setCurrentMusic(item.url)"
          :id="index"
        >
      </div>
    </div>
  </div>
</template>
<script>
const { music } = require("@/assets/utils/mock-data");
export default {
  data() {
    return {music};
  },
  inject:['setCurrentMusic'],
  methods:{
      playMusic(){

      }
  }
};
</script>
<style lang="less" scoped>
@import "~@/assets/less/tool.less";
.mi_con {
  width: 95%;
  height: 90%;
  overflow: auto;
  margin: 0 auto;
}
.item {
  margin: 10px auto;
  display: flex;
  align-items: center;
  border-bottom: 2px solid #ffee7c;
  width: 450px;
  height: 128px;
  justify-content: space-between;
  /* border-radius: 10px; */
  /* padding: 5px 0; */
}
.item .item_cover {
  width: 88px;
  height: 88px;
  border-radius: 10px;
  margin-left: 5px;
}
.music_info_con {
  display: flex;
}
.music_info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 20px;
}
.mo_name {
  font-size: 30px;
  color: #ff663a;
}
.mo_singer {
  font-size: 25px;
  color: #ccc;
}
.mo_play {
  width: 50px;
  height: 50px;
  /* margin-left:150px; */
  float: right;
}
</style>


