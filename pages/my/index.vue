<template>
  <view>
    <view class="vmb-my-header">
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
    </view>
    <view class="vmb-my-nav">
      <u-grid :border="false" :col="4" hover-class="hover-class">
        <u-grid-item v-for="(item, index) in list" :index="index" :key="index">
          <u-icon :name="item" :size="46"></u-icon>
          <text class="grid-text">{{ '宫格' + (index + 1) }}</text>
        </u-grid-item>
      </u-grid>
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
        list: ['integral', 'kefu-ermai', 'coupon', 'gift', ],
        pic: 'https://i.gtimg.cn/club/item/face/img/2/15922_100.gif',
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
  .vmb {
    &-my-header {
      box-sizing: border-box;
      width: 100%;
      height: 300rpx;
      background: url("~@/static/my/header.png");
      background-size: 100% 100%;
      padding: 60rpx 30rpx;
      border-radius: 0 0 60rpx 60rpx;

      ::v-deep {
        .u-avatar {
          border: 2px solid #FFFFFF;
        }

        .u-p-b-20 {
          color: #FFFFFF
        }

        .u-tips-color {
          color: #FFFFFF
        }

        .u-icon__icon {
          color: #FFFFFF !important
        }


      }
    }

    &-my-nav {
      width: calc(100% - 60rpx);
      margin-left: auto;
      margin-right: auto;
      height: 150rpx;
      background: linear-gradient(to right, #1b3185, #01235a);
      margin-top: -80rpx;
      border-radius: 20rpx;

      ::v-deep {
        .u-grid {

          .u-grid-item {
            background: transparent !important;
            color: #FFFFFF !important;
          }
        }
      }
    }
  }
</style>
