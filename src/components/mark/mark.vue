<template>
  <div id="markContainer" :style="{width,height}">
    <img :src="loadingImg" class="loading-img" :class="{'hide-loading': !isLoading}">
    <img :src="imgUrl" id="containerImg" v-show="!isLoading" :class="{'show-container-img': !isLoading}">
  </div>
</template>
<script>
import $ from 'jquery';
import './mark-config';
export default {
  name: 'VueMarkImage',
  props: {
    // 默认宽度
    width: {
      type: String,
      default: '850px'
    },
    // 默认高度
    height: {
      type: String,
      default: '850px'
    },
    // 图片地址
    imgUrl: {
      type: String
    },
    // 默认颜色
    defaultColor: {
      type: String,
      default: '#666'
    },
    // 默认锚点数据
    markList: {
      type: Array,
      default: () => {
        return [];
      }
    }
  },
  data() {
    return {
      isLoading: true,
      loadingImg: require('@/assets/images/loading.png')
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    //初始化数据
    init() {
      setTimeout(() => {
        this.isLoading = false;
        $('#markContainer').ZoomMark({
          markList: this.markList,
          markColor: this.defaultColor,
          afterMark: this.addRowToTabel,
          disabled: false,
          itemClick: this.itemClick
        });
      }, 3000);
    },
    addRowToTabel(){      
      this.changeMark();
    },
    // 锚点点击事件
    itemClick(markId){
      this.$emit('click', markId);
    },
    // 删除锚点
    deleteMark(markIds) {
      markIds.map(markId => {
        $('#markContainer').ZoomMark('deleteMark', markId);
      });
      this.changeMark();
    },
    // 锚点改变
    changeMark(){
      let arrayList = $('#markContainer').ZoomMark('getMark');
      this.$emit('change', arrayList);
    },
    // 设置锚点颜色
    setMarkColor(markIds, color){
      markIds.map(markId => {
        $(`#markContainer #mark_${markId}`).css('background-color', color);
      });      
    }
  }
};
</script>
<style lang="less" scoped>
 @keyframes rotateAnimation {
  0% {
    transform: rotate(0);
    opacity: 0;
  }
  50% {
    opacity: 1;
    transform: rotate(360deg);
  }
  100% {
    opacity: 0;
    transform: rotate(720deg);
  }
}
#markContainer{
	display: inline-block;
  background-image: url('~@/assets/images/transparent.png');
  overflow: hidden;
  position: relative;
  .loading-img{
    position: absolute;
    z-index: 2;
    width: 150px;
    height: 150px;
    top: 50%;
    left: 50%;
    margin-top: -75px;
    margin-left: -75px;
    translate: all 0.4s;
    animation: rotateAnimation 4s infinite;
    &.hide-loading{
      opacity: 0;
      visibility: hidden;
    }
  }
  #containerImg{
    transition: all 0.5s;
    transform: scale(3);
    &.show-container-img{
      transform: scale(1);
    }
  }
}
/deep/.vue-mark {
  width: 30px;
  height: 30px;
  position: absolute;
  transform: translate(-50%, -50%);
  color: rgb(255, 255, 255);
  text-align: center;
  line-height: 30px;
  opacity: 0.8;
  border-radius: 50%;
  transition: all 0.4s;
}
</style>
