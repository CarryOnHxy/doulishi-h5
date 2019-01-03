<template>
  <div class="upload-pic-con">
    <div  :class="currentPicAnimation+' pic_con'" ref="picsCon" 
    :style="{backgroundImage:'url('+picUrl[currentPic]+')'}"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentPicAnimation: "pic-animation",
      currentAnimationIndex: 0,
      currentPic: 0 
    };
  },
  mounted(){
    console.log('mounted',this) 
    let picsCon = this.$refs['picsCon'];
    // return
    this.adaptAnimation(picsCon,this.changeCurrentPic)
  },
  methods: {
    changeCurrentPic: function() {
      let picUrl = this.picUrl,
        currentPic = this.currentPic;
      if (!currentPic || currentPic == -1) {
        currentPic = picUrl.length - 1;
      } else {
        currentPic--;
      }
      let currentAnimationIndex = this.currentAnimationIndex,
        currentPicAnimation = null;
      console.log("currentAnimationIndex", currentAnimationIndex);
      currentAnimationIndex = (++currentAnimationIndex) % 5;
      switch (currentAnimationIndex) {
        case 0:
          currentPicAnimation = "pic-animation";
          break;
        case 1:
          currentPicAnimation = "pic-animation2";
          break;
        case 2:
          currentPicAnimation = "pic-animation3";
          break;
        case 3:
          currentPicAnimation = "pic-animation5";
          break;
        case 4:
          currentPicAnimation = "pic-animation4";
      }
      this.currentPic = currentPic;
      this.currentAnimationIndex = currentAnimationIndex;
      this.currentPicAnimation = currentPicAnimation;
    },
    adaptAnimation: function(dom, functionName) {
      let prefixArr = ["webkit", "moz", "MS", "o", ""];
      prefixArr.forEach(ele => {
        dom.addEventListener(`${ele}animationiteration`, functionName);
      });
    }
  },
  props: ["picUrl"]
};
</script>
<style lang="less" scoped>
.upload-pic-con {
  position: absolute;
  top: 365px;
  left: 50%;
  width: 500px;
  height: 707px;
  margin-left: -250px;
  /* border: #f3ba4f solid 5px; */
  border-radius: 5%;
  display: inline-block;
  z-index: 0;
}
.upload-pic-con .pic_con {
  width: 100%;
  height: 100%;
  border-radius: 5%;
  position: absolute;
  background-size: cover;
  background-position: center 0;
  animation-duration: 8s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

.pig-animation {
  animation-name: pig-animation;
  animation-duration: 8s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

.pic-animation {
  animation-name: pic-animation;
}

.pic-animation2 {
  animation-name: pic-animation2;
}

.pic-animation3 {
  animation-name: pic-animation3;
}

.pic-animation4 {
  animation-name: pic-animation4;
}

.pic-animation5 {
  animation-name: pic-animation5;
}

.pic-animation6 {
  animation-name: pic-animation6;
}

.pic-animation7 {
  animation-name: pic-animation7;
}

@keyframes pic-animation {
  0% {
    opacity: 0;
    transform: skew(-30deg, -30deg);
  }

  50% {
    opacity: 1;
    transform: scale(1.5, 1.5);
  }

  80% {
    opacity: 1;
    transform: scale(1, 1);
  }

  100% {
    opacity: 1;
    transform: scale(1, 1);
  }
}

@keyframes pic-animation2 {
  0% {
    opacity: 0;
    transform: scale(0.5, 0.5);
  }

  50% {
    opacity: 1;
    transform: scale(1.5, 1.5);
  }

  80% {
    opacity: 1;
    transform: scale(1, 1);
  }

  100% {
    opacity: 1;
    transform: scale(1, 1);
  }
}

@keyframes pic-animation3 {
  0% {
    opacity: 0;
    transform: skew(60deg, 60deg);
  }

  50% {
    opacity: 1;
    transform: scale(1.5, 1.5);
  }

  80% {
    opacity: 1;
    transform: scale(1, 1);
  }

  100% {
    opacity: 1;
    transform: scale(1, 1);
  }
}

@keyframes pic-animation4 {
  0% {
    opacity: 1;
    transform: translateX(0px) rotate(0deg);
  }

  100% {
    opacity: 0;
    transform: translateX(-500px) rotate(360deg);
  }
}

@keyframes pic-animation5 {
  0% {
    opacity: 1;
    transform: translateX(0px) rotate(0deg);
  }

  100% {
    opacity: 0;
    transform: translateX(500px) rotate(360deg);
  }
}

@keyframes pic-animation6 {
  0% {
    opacity: 1;
    transform: translateY(0px) rotate(0deg);
  }

  100% {
    opacity: 0;
    transform: translateY(500px) rotate(360deg);
  }
}

@keyframes pic-animation7 {
  0% {
    opacity: 1;
    transform: translateY(0px);
  }

  100% {
    opacity: 0;
    transform: translateY(-500px);
  }
}

@keyframes pig-animation {
  0% {
    transform: translateX(100px);
  }

  100% {
    transform: translateX(-1000px);
  }
}
</style>

