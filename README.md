## Install

Using npm:
```
npm install vue-mark-image --save

import VueMarkImage from 'vue-mark-image';
Vue.use(VueMarkImage);

```

## Usage

```vue
<template>
  <VueMarkImage ref="vueMarkRef" :imgUrl="imgUrl" :markList="markList" @on-change="onChange" @click="clickMark" />
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
```

## API AreaSelect
## props
属性|说明|类型|默认值
:-------: | -------  |  :-------:  |  :-------:
width |  默认宽度  | String |  850px
height |  默认高度  | String |  850px
imgUrl |  图片地址，网络地址或base64  | String |  -
defaultColor |  默认颜色，十六进制颜色码  | String |  #666
markList |  默认锚点数据  | Array |  例子[{id: 1,x: 320.9479064941406,y: 222.3333282470703,color: 'red'}]

## events
事件名|说明|返回值|返回值参数说明
:-------: | -------  |  :-------:  |  :-------:
change |  增加或删除锚点时触发  | Function | 返回值，数组，如[{id: 1,x: 320.9479064941406,y: 222.3333282470703,color: 'red'}]
click |  锚点点击事件  | Function | 返回值，锚点id


Copyright (c) 2020-05-29, 32237384@qq.com
