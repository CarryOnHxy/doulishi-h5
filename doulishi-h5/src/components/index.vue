<template>
  <div class="container">
    <index-con>
      <index-menu :pic-url="picUrl"></index-menu>
      <button class="to_do_btn">逗利是</button>
      <pig />
    </index-con>
  </div>
</template>
<script>
import indexCon from "./common/index-con.vue";
import indexMenu from "./common/index-menu.vue";
import pig from "./main/pig.vue";
export default {
  data() {
    return {
      picUrl: []
    };
  },
  components: { indexCon, indexMenu, pig }
};
</script>
<style lang="less" scoped>
@import (less) "../assets/less/tool.less";
.container {
  .wh(100vw, 100vh);
  overflow: hidden;
}
.to_do_btn {
  width: 510px;
  height: 88px;
  border-radius: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffee7c;
  position: absolute;
  bottom: 120px;
  left: 50%;
  margin-left: -255px;
  box-shadow: 0 5px 1px 1px rgba(0, 0, 0, 0.13);
  outline: none;
  border: none;
  font-size: 36px;
  color: #ff663a;
}
</style>

