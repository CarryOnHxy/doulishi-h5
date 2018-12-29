<template>
  <div class="menu">
    <div @click="displayMediaList" id="music">
      <img src="@/assets/images/v2/music.png">
    </div>
    <div :class="{chooseClass}" @click="displayMediaList" id="pics" style="position:relative">
      <img src="@/assets/images/v2/pics.png" v-if="picUrl.length<=0">
      <span v-else>{{picUrl.length}}</span>
      <label class="menu_choose_pic" for="choosePic" v-if="picUrl.length<=0"></label>
      <input type="file" name="pics" id="choosePic" hidden @change="selectImg">
    </div>
    <div @click="toMine" id="mine">
      <img src="@/assets/images/v2/mine.png">
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  computed: {
    chooseClass() {
      console.log("chooseClass", arguments, this);
      return {
        "choose-pic": this.picUrl.length > 0
      };
    }
  },
  props: ["musicSwitch", "picUrl"],
  methods: {
    displayMediaList() {},
    toMine() {},
    selectImg(flies) {

      console.log("files in SelcetImg", flies,this.$el);
    }
  }
};
</script>
<style lang="less" scoped>
@import url("../../assets/less/tool.less");
.menu {
  position: absolute;
  top: 290px;
  right: 29px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.menu img {
  width: 70px;
  height: 70px;
}
.menu div {
  margin-bottom: 24px;
}
.menu_choose_pic {
  display: block;
  .wh(70px, 70px);
  .ab(t, 0);
  opacity: 0;
}
.music-rotate {
  animation: music-rotate 5s linear infinite;
}
.choose-pic {
  border: 1px solid #ffe97a; /* px */
  background-color: rgba(0, 0, 0, 0.424);
  border-radius: 50%;
  width: 70px;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  color: #ffee7c;
  position: relative;
}
@keyframes music-rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>

