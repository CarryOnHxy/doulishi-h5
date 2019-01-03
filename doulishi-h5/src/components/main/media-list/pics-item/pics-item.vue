<template>
  <div class="pics_con">
    <div class="pics_item_wrap" v-if="temPicUrl.length>0">
      <div class="pics_item" v-for="(item,index) of temPicUrl" :key="index">
        <img class="pics_pic" :src="item">
        <div class="pics_options">
          <img class="option" @click="upPic" :id="index" src="@/assets/images/v2/up.png">
          <img class="option" @click="downPic" :id="index" src="@/assets/images/v2/down.png">
          <img class="option" @click="deletePic" :id="index" src="@/assets/images/v2/delete.png">
        </div>
      </div>
    </div>
    <div class="pics_item_none" v-else>无图片</div>
    <label for="addPic" class="pics_add_btn">
      <img src="@/assets/images/v2/add.png">
    </label>
    <input type="file" id="addPic" multiple hidden @change="selectImg">
  </div>
</template>
<script>
export default {
  data() {
    return {
      /* 给予来自祖先组件的依赖注入默认值 */
      temPicUrl:[]
    };
  },
  watch: {
    picUrl(newVal, oldVal) {
      console.log('newVal',newVal);
    }
  },
  inject: ["displayMediaList", "setPicUrl","getPicUrl"],
  created(){
    this.temPicUrl = JSON.parse(JSON.stringify(this.getPicUrl()))
    return
  },
  beforeDestroy(){
    this.setPicUrl(this.temPicUrl)
  },
  methods: {
    upPic(e) {
      let index = e.target.id;
      let temPicUrl = this.temPicUrl;
      if (index != 0) {
        let tmp = temPicUrl[index - 1];
        temPicUrl[index - 1] = temPicUrl[index];
        temPicUrl.splice(index, 1, tmp);
      } else {
        let tmp = temPicUrl[temPicUrl.length - 1];
        temPicUrl[temPicUrl.length - 1] = temPicUrl[index];
        temPicUrl.splice(index, 1, tmp);
      }
      this.temPicUrl = temPicUrl;
    },
    downPic(e) {
      let index = e.target.id * 1;
      let temPicUrl = this.temPicUrl;
      if (index != temPicUrl.length - 1) {
        let tmp = temPicUrl[index + 1];
        temPicUrl[index + 1] = temPicUrl[index];
        temPicUrl.splice(index, 1, tmp);
      } else {
        let tmp = temPicUrl[0];
        temPicUrl[0] = temPicUrl[index];
        temPicUrl.splice(index, 1, tmp);
      }
      console.log("downPic", temPicUrl);
      this.temPicUrl = temPicUrl;
    },
    deletePic(e) {
      let index = e.target.id * 1;
      let temPicUrl = this.temPicUrl;
      temPicUrl.splice(index, 1);
      this.temPicUrl = temPicUrl;
    },
    selectImg(e) {
      // console.log("event", e);
      [].forEach.call(e.target.files, this.readAndPreview);
    },
    /* 上传图片 */
    readAndPreview(file) {
      let reader = new FileReader();
      reader.addEventListener("load", e => {
        let fileResult = reader.result,
          temPicUrl = this.temPicUrl;
        if (temPicUrl.indexOf(fileResult) == -1 && temPicUrl.length < 8) {
          temPicUrl.push(fileResult);
        }
      });
      if (/\.(jpe?g|png|bmp)$/i.test(file.name)) reader.readAsDataURL(file);
    }
  }
};
</script>
<style lang="less" scoped>
@import "~@/assets/less/tool.less";
.pics_con {
  width: 95%;
  height: 92%;
  /* overflow:auto; */
  margin: 0 auto;
  position: relative;
}
.pics_item_wrap {
  overflow: auto;
  width: 100%;
  height: 80%;
}
.pics_item {
  margin: 10px auto;
  width: 450px;
  height: 128px;
  display: flex;
  align-items: center;
  border-bottom: 2px solid #ffee7c; /* px */
  justify-content: space-between;
  border-radius: 10px; /* px */
  padding: 15px 0;
}
.pics_pic {
  width: 116px;
  height: 116px;
  margin-left: 10px;
  border-radius: 10px; /* px */
}
.pics_options {
  display: flex;
  justify-content: space-around;
  margin-right: 20px;
  height: 60px;
}
.pics_options img {
  width: 52px;
  height: 52px;
}
.pics_options img:nth-child(2) {
  margin: 0 22px;
}
.reference {
  position: relative;
}
.pics_add_btn {
  position: absolute;
  bottom: 32px;
  left: 0;
  right: 0;
  margin: auto;
  display: block;
  text-align: center;
}
.pics_add_btn img {
  width: 56px;
  height: 56px;
}
.pics_item_none {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 100%;
  text-align: center;
  font-size: 45px;
  color: #ccc;
}
</style>

