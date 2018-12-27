<template>
  <div class="index_con">
    <image src="\static\avatar.png" class="index_coin" />
    <!-- <image src="/images/v2/firecrackers.png" class="firecrackers" /> -->
    <!-- <image src="/images/v2/2019.png" class="year" /> -->
    <!-- <image src="/images/v2/red-packet-man.png" class="red-packet-man" /> -->
    <!-- <image src="/images/v2/yuanbao.png" class="yuanbao" /> -->
    <!-- <image src="../../images/lantern.png" class="lantern" /> -->
    <!-- <button>逗利是</button>  -->
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
  background-size: 100%;
  background-repeat: no-repeat;
  position: relative;
  border: green solid 1px /* no */
}
.index_coin {
  // position: absolute;
  // top: 355px;
  // left: 142px;
  // width: 39px;
  // height: 65px;
  // z-index: 150;
}
</style>

