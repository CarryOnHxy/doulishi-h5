<template>
  <div class="list_bg">
    <div class="list_con">
      <img class="list_close" src="@/assets/images/v2/close.png" @click="displayMediaList">
      <pics-item v-if="mediaType == 'pics'"/>
      <music-item v-else />
    </div>
  </div>
</template>
<script>
import picsItem from "./pics-item/pics-item.vue";
import musicItem from './music-item/music-item.vue'
export default {
  inject: ["displayMediaList"],
  props:['mediaType'],
  methods: {},
  components: { picsItem,musicItem }
};
</script>
<style lang="less" scoped>
@import "~@/assets/less/tool.less";
.list_bg {
  width: 100%;
  height: 100%;
  /* background-color:transparent;  */
  background-color: rgba(204, 204, 204, 0.397);
  .ab(t, 0);
  z-index: 500;
}
.list_close {
  width: 30px;
  height: 30px;
  margin: 20px auto auto 20px;
}

.list_con {
  width: 517px;
  height: 740px;
  background-color: #fff8c6;
  border-radius: 10px;
  .po_cet();
}
.music_item {
  width: 100%;
  height: 100%;
}
</style>

