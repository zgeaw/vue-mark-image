<template>
  <div id="markContainer" :style="{width,height}">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfQAAAH0CAYAAADL1t+KAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYxIDY0LjE0MDk0OSwgMjAxMC8xMi8wNy0xMDo1NzowMSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNS4xIFdpbmRvd3MiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MUJENUY1QUNBMThFMTFFQUEwREJGMkExNDk2QUU1RkMiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MUJENUY1QURBMThFMTFFQUEwREJGMkExNDk2QUU1RkMiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxQkQ1RjVBQUExOEUxMUVBQTBEQkYyQTE0OTZBRTVGQyIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxQkQ1RjVBQkExOEUxMUVBQTBEQkYyQTE0OTZBRTVGQyIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PhsTUHQAACuXSURBVHja7N0J3GZj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" class="loading-img" :class="{'hide-loading': !isLoading}">
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
      isLoading: true
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
