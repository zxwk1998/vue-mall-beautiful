<template>
  <view>
    <view class="u-flex user-box u-p-l-30 u-p-r-20 u-p-b-30">
      <view class="u-m-r-10">
        <u-avatar :src="pic" size="140"></u-avatar>
      </view>
      <view class="u-flex-1">
        <view class="u-font-18 u-p-b-20">vue-mall-beautiful</view>
        <view class="u-font-14 u-tips-color">微信号:vue-mall-beautiful</view>
      </view>
      <view class="u-m-l-10 u-p-10">
        <u-icon name="arrow-right" color="#969799" size="28"></u-icon>
      </view>
    </view>

    <view class="u-m-t-20">
      <u-cell-group>
        <u-cell-item @tap="openPage('pages/my/address')" icon="map" title="收货地址"></u-cell-item>
      </u-cell-group>
    </view>

    <view class="u-m-t-20">
      <u-cell-group>
        <u-cell-item icon="coupon" title="卡券"></u-cell-item>
      </u-cell-group>
    </view>

    <view class="u-m-t-20">
      <u-cell-group>
        <u-cell-item icon="setting" title="设置"></u-cell-item>
      </u-cell-group>
    </view>
    <view class="u-m-t-20">
      <u-cell-group>
        <u-cell-item icon="" title="时间原因未来的及重构当前页面,敬请期待"></u-cell-item>
      </u-cell-group>
    </view>
    <view class="u-m-t-20">
      <u-cell-group>
        <u-cell-item icon="" title="vue-mall-beautiful基于uview开发"></u-cell-item>
      </u-cell-group>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        pic: 'https://uviewui.com/common/logo.png',
        show: true
      }
    },
    onLoad() {

    },
    methods: {
      openPage(path) {
        this.$u.route({
          url: path
        })
      },
    }
  }
</script>

<style lang="scss">
  page {
    background-color: #ededed;
  }

  .camera {
    width: 54px;
    height: 44px;

    &:active {
      background-color: #ededed;
    }
  }

  .user-box {
    background-color: #fff;
  }
</style>
