<template>
  <div>
    <VueMarkImage ref="vueMarkRef" :imgUrl="imgUrl" :markList="markList" @change="changeMark" @click="clickMark" />
    <button @click="changeMarkColor">改变锚点1颜色</button>
    <button @click="deleteMark">删除锚点1</button>
  </div>
</template>
<script>
  import { VueMarkImage } from 'VueMarkImage';
  export default {
    components: { VueMarkImage },
    data(){
      return {
        imgUrl: require('../assets/images/2d.jpg'),
        markList: [
          {
            id: 11,
            x: 320.9479064941406,
            y: 222.3333282470703,
            color: 'red'
          },
          {
            id: 22,
            x: 527.9479064941406,
            y: 292.3333282470703,
            color: 'red'
          }
        ]
      };
    },
    mounted(){},
    methods: {
      // 锚点改变
      changeMark(array){
        console.log('锚点改变', array);
      },
      // 设置锚点颜色
      changeMarkColor(){
        this.$refs.vueMarkRef.setMarkColor([11, 22], 'green');
      },
      // 删除锚点
      deleteMark(){
        this.$refs.vueMarkRef.deleteMark([11, 22]);
      },
      // 锚点点击
      clickMark(markId){
        console.log('点击了', markId);
      }
    }
  };
</script>
