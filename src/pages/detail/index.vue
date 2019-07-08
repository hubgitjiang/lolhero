<template>
  <div>
    <!-- 轮播图 -->
    <swiper indicator-dots autoplay interval="3000" duration="300" circular>
      <block v-for="(item,index) in heroObj.bgs" :key="index">
        <swiper-item class="item">
          <image mode="aspectFill" :src="item" class="slide-image" />
        </swiper-item>
      </block>
    </swiper>
    <view class="box">
      <view class="left">
        <view class="title"> {{ heroObj.title }} </view>
        <view class="name">{{ heroObj.name }}</view>
        <block>
          <text v-for="(item, index) in heroObj.tags" :key="index" class="tag">{{item}}</text>
        </block>
        <block>
          <view class="ab">
            <text>生存能力</text>
            <progress active :percent="heroObj.Ability.life" color="#1eca6b" backgroundColor="#363c3c" stroke-width="12"></progress>
          </view>
          <view class="ab">
            <text>物理攻击</text>
            <progress active :percent="heroObj.Ability.physical" color="#f2c500" backgroundColor="#363c3c" stroke-width="12"></progress>
          </view>
          <view class="ab">
            <text>魔法攻击</text>
            <progress active :percent="heroObj.Ability.magic" color="#f59d00" backgroundColor="#363c3c" stroke-width="12"></progress>
          </view>
          <view class="ab">
            <text>操作难度</text>
            <progress active :percent="heroObj.Ability.difficulty" color="#cb8cff" backgroundColor="#363c3c" stroke-width="12"></progress>
          </view>
        </block>
      </view>
      <view class="right">
        {{ heroObj.story }}
      </view>
    </view>
  </div>
</template>

<script>
import detailList from '../../utils/lol_details_duowan.js'

export default {
  data() {
    return {
      detailList: detailList,
      heroObj: {
        Ability: {}
      }
    }
  },
  // 接收参数
  // 在 mpvue 中不建议使用小程序的生生命周期
  // onLoad(option) {
  //   console.log(option)
  // }
  mounted() {
    // 获取 id
    let id = this.$root.$mp.query.id
    // 遍历数据
    this.heroObj = this.detailList.filter(item => {
      return item.id === id
    })[0]
    console.log(this.heroObj)
  }
}
</script>

<style>
/* pages/detail/detail.wxss */

page {
  color: white;
  background-color: #343434;
  font-size: 12px;
}

.item image {
  width: 100%;
}

.box {
  display: flex;
}

.box .left {
  flex: 1;
  padding: 10px;
  height: 100px;
}

.box .left .title {
  font-size: 14px;
  font-weight: 700;
}

.box .left .name {
  font-size: 24px;
  font-weight: 700;
}

.box .left .tag {
  display: inline-block;
  font-size: 12px;
  background-color: #099d7e;
  padding: 2px 4px;
  border-radius: 3px;
  margin: 10px 5px 10px 0px;
}

.box .left .ab {
  display: flex;
}

.box .left .ab text {
  flex: 1;
}

.box .left .ab progress {
  flex: 2;
}

.box .right {
  flex: 1;
  padding: 5px;
}
</style>
