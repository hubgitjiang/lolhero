<template>
    <div class="mybox">
        <!-- 
                        在 mpvue 中：
                            书写页面结构时可以使用 html + css 
                                        也可以使用 wxml 中的组件
                       -->
        <div v-for="(item, index) in dataList" :key="index" class="item">
            <a :href="'/pages/detail/main?id=' + item.id">
                <img :src="item.iconUrl" alt="">
                <p>{{ item.name }}</p>
            </a>
        </div>
        <!-- 小程序的组件 -->
        <!-- <div class="item">
                          <image src="https://ossweb-img.qq.com/images/lol/img/champion/Sylas.png"></image>
                          <text>塞拉斯</text>
                      </div> -->
    </div>
</template>

<script>
// 遵守 commonjs
//   require
//   module.export
// vue:  ES6
// import 
// export default

import dataList from '../../utils/lol_duowan.js'
export default {
    data() {
        return {
            dataList: dataList
        }
    },
    mounted() {
        console.log(wx)
    }
}
</script>

<style scoped lang="less">
.mybox {
    display: flex;
    flex-wrap: wrap;
    .item {
        width: 33.33%;
        text-align: center;
        img {
            width: 100px;
            height: 100px;
            ;
        }
    }
}
</style>
