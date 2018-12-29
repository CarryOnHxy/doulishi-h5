<template>
  <div class="index_con">
    <img src="@/assets/images/v2/coin.png" class="index_coin">
    <img src="@/assets/images/v2/firecrackers.png" class="firecrackers">
    <img src="@/assets/images/v2/2019.png" class="year">
    <img src="@/assets/images/v2/red-packet-man.png" class="red-packet-man">
    <img src="@/assets/images/v2/yuanbao.png" class="yuanbao">
    <img src="@/assets/images/lantern.png" class="lantern">
    <slot></slot>
  </div>
</template>
<script>
export default {};
</script>
<style lang="less" scoped>
@import "../../assets/less/tool.less";
.index_con {
  .wh(100%, 100%);
  background-image: url(../../assets/images/v2/bg.png);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center 0;
  position: relative;
}
.index_coin {
  position: absolute;
  top: 355px;
  left: 142px;
  width: 39px;
  height: 65px;
  z-index: 150;
}
.coin {
  position: absolute;
  top: 355px;
  left: 142px;
  width: 39px;
  height: 65px;
  z-index: 150;
}
.firecrackers {
  position: absolute;
  top: 420px;
  left: 0px;
  width: 140px;
  height: 421px;
}
.red-packet-man {
  position: absolute;
  top: 133px;
  left: 0;
  right: 0;
  margin: auto;
  height: 137px;
  width: 137px;
}
.yuanbao {
  width: 57px;
  height: 47px;
  position: absolute;
  bottom: 465px;
  right: 91px;
}
.year {
  position: absolute;
  bottom: 0;
  top: 0;
  left: 0;
  right: 0;
  margin: auto;
  width: 375px;
  height: 257px;
}
.lantern {
  position: absolute;
  height: 362px;
  width: 148px;
  top: 0px;
  left: 37px;
  z-index: 150;
}

</style>

