<template>
  <div class="container">
    <index-con>
      <index-menu :pic-url="picUrl" :music-state="musicState"/>
      <pig :pic-url-length="picUrl.length" />
      <media-list
        @displayMediaList="displayMediaList"
        v-if="showMediaList"
        :media-type="mediaType"
        :pic-url="picUrl"
        v-on:set-pic-url="setPicUrl"
      />
      <album  :pic-url="picUrl" v-show="picUrl.length>0" ref="album"/>
      <button class="to_do_btn">{{inIndex?'逗利是':'发利是'}}</button>
      <audio :src="currentMusic" muted ref="musicPlayer" controls autoplay></audio>
      <div class="redpacket-info" v-if="!inIndex">
        <!-- <img :src="redPacketInfo.userHeadImg">
        <span>{{redPacketInfo.userName}} 给你拜年逗利是啦</span>-->
        <img src="@/assets/images/avatar.png">
        <span class="text">Carry On Hxy 给你拜年逗利是啦</span>
      </div>
    </index-con>
  </div>
</template>
<script>
import indexCon from "./common/index-con.vue";
import indexMenu from "./common/index-menu.vue";
import pig from "./main/pig.vue";
import album from "./main/album.vue";
import mediaList from "./main/media-list/media-list.vue";
const { music } = require("@/assets/utils/mock-data");
export default {
  data() {
    return {
      picUrl: [],
      showMediaList: false,
      mediaType: "",
      currentMusic: "",
      inIndex: true,
      musicState: true,
      music
    };
  },
  components: { indexCon, indexMenu, pig, album, mediaList },
  watch: {
    picUrl(newVal, oldVal) {
      console.log("父组件的picUrl", newVal);
      /* 删除或者增加图片时从第一张开始播放，避免播放中的图片突然被删 */
      if(newVal.length != oldVal.length){
        this.$refs['album'].currentPic = 0;
      }
    }
  },
  mounted() {
    let defaultMusic = music[0];
    defaultMusic.isPlayed = true;
    this.setCurrentMusic(defaultMusic);
  },
  methods: {
    displayMediaList(mediaType) {
      // console.log('displayMediaList ing')
      if (this.inIndex) {
        this.showMediaList = !this.showMediaList;
        if (mediaType) this.mediaType = mediaType;
      }
    },
    setPicUrl(newPicUrl) {
      console.log('newPicUrl');
      this.picUrl = newPicUrl;
    },
    getPicUrl(){
      console.log('getPicUrl');
      
      return this.picUrl
    },
    setCurrentMusic(newMusic, callback) {
      let musicPlayer = this.$refs["musicPlayer"];
      callback && callback();
      // console.log('newMusic',newMusic);
      this.currentMusic = newMusic.url;
      this.musicState = newMusic.isPlayed;
      if (newMusic.isPlayed) {
        console.dir(musicPlayer);
          musicPlayer.play();
      } else musicPlayer.pause();
    },
    setMusicState(musicState) {
      this.musicState = musicState;
    }
  },
  provide() {
    return {
      displayMediaList: this.displayMediaList,
      setPicUrl: this.setPicUrl,
      setCurrentMusic: this.setCurrentMusic,
      inIndex: this.inIndex,
      setMusicState: this.setMusicState,
      picUrl: this.picUrl,
      getPicUrl:this.getPicUrl
    };
  }
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
.redpacket-info {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 110px;
}

.redpacket-info img {
  height: 74px;
  width: 74px;
  border-radius: 50%;
  border: 1px solid #ffe63a; /* no */
  margin-bottom: 10px;
}

.redpacket-info .text {
  font-size: 28px; /* px */
  color: #ff663a;
  margin-left: 4px;
}
</style>

