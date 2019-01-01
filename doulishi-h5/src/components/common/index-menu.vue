<template>
  <div class="menu">
    <div @click="displayMediaList('music')" id="music">
      <img src="@/assets/images/v2/music.png">
    </div>
    <div :class="chooseClass" @click="displayMediaList('pics')" id="pics" style="position:relative">
      <img src="@/assets/images/v2/pics.png" v-if="picUrl.length<=0" />
      <span v-else>{{picUrl.length}}</span>
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
  watch: {
    picUrl(newVal, oldVal) {
      console.log("picUrl newVal", newVal);
    }
  },
  inject:['displayMediaList'],
  props: {
    musicSwitch: {
      default: false
    },
    picUrl: {
      default: []
    }
  },
  methods: {
    toMine() {}
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
  border: 2px solid #ffe97a; /* px */
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

