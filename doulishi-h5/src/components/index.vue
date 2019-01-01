<template>
  <div class="container">
    <index-con>
      <index-menu :pic-url="picUrl"></index-menu>
      <button class="to_do_btn">逗利是</button>
      <pig :pic-url-length="picUrl.length"/>
      <media-list @displayMediaList="displayMediaList" v-if="showMediaList" :media-type="mediaType"/>
      <album :pic-url="picUrl" v-if="picUrl.length>0"/>
        <audio :src="currentMusic" muted autoplay ref="musicPlayer"></audio>
    </index-con>
  </div>
</template>
<script>
import indexCon from "./common/index-con.vue";
import indexMenu from "./common/index-menu.vue";
import pig from "./main/pig.vue";
import album from './main/album.vue';
import mediaList from './main/media-list/media-list.vue'
export default {
  data() {
    return {
      picUrl: [],
      showMediaList:false,
      mediaType:'',
      currentMusic:''
    };
  },
  components: { indexCon, indexMenu, pig,album,mediaList},
  methods:{
    displayMediaList(mediaType){
      console.log('displayMediaList ing')
      this.showMediaList = !this.showMediaList;
      if(mediaType) this.mediaType = mediaType
    },
    setPicUrl(newPicUrl){
      this.picUrl = newPicUrl
    },
    setCurrentMusic(newMusic){
      this.currentMusic = newMusic;
      console.log(this.$refs);
      
      this.$refs['musicPlayer'].play()
    }
  },
  provide(){
    return {
      displayMediaList:this.displayMediaList,
      setPicUrl:this.setPicUrl,
      setCurrentMusic:this.setCurrentMusic
    }
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
</style>

