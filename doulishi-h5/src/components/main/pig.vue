<template>
  <div :class="{'pig-blessing':true,'pig-animation':picUrlLength>0}" ref="pigCon">
    <img src="@/assets/images/pig-bg2.png" class="pig">
    <span v-if="picUrlLength>0" class="blessing">{{blessingText[blessingTextIndex]}}</span>
  </div>
</template>
<script>
const {blessingText} = require('@/assets/utils/mock-data.js')
export default {
  data() {
    return {
      blessingText,
      blessingTextIndex: 0
    };
  },
  computed: {

  },
  props: { picUrlLength: { default: -1 } },
  mounted() {
    let picCon = this.$refs["pigCon"];
    let that = this;
    function afterAnimaitionCycle() {
      //   console.log("afterAnimaitionCycle", that.$data);
      let blessingTextIndex = that.blessingTextIndex;
      if (!blessingTextIndex) {
        blessingTextIndex = 0;
      }
      blessingTextIndex += 1;
      blessingTextIndex = blessingTextIndex % that.picUrlLength;
      that.blessingTextIndex = blessingTextIndex;
      //   console.log("change blessingIndex", blessingTextIndex, that);
    }
    this.adaptAnimation(picCon, afterAnimaitionCycle);
  },
  methods: {
    adaptAnimation: function(dom, functionName) {
      let prefixArr = ["webkit", "moz", "MS", "o", ""];
      prefixArr.forEach(ele => {
        dom.addEventListener(`${ele}animationiteration`, functionName);
      });
    }
  }
};
</script>
<style lang="less" scoped>
@import "~@/assets/less/tool.less";
.pig-blessing {
  position: absolute;
  bottom: 209px;
  right: 0px;
  .fl_cet();
  z-index: 800
}
.pig {
  width: 210px;
  height: 220px;
}
.blessing {
  color: #ffee7c;
  margin-left: 20px;
  font-size: 45px; /* px */
}
.pig-animation {
  animation: pig-animation 8s linear infinite;
  right: -223px;
}
@keyframes pig-animation {
  0% {
    transform: translateX(0px);
  }
  100% {
    transform: translateX(-1000px);
  }
}
</style>

