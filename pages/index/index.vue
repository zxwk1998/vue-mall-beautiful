<template>
  <view class="vmb-container">
    <view class="vmb-search" v-if="searchShow">
      <u-navbar :is-back="false" title="vue-mall-beautiful">
      </u-navbar>
      <u-search placeholder="" v-model="keyword"></u-search>
    </view>
    <view class="vmb-search2" v-if="searchShow2">
      <u-search placeholder="" v-model="keyword"></u-search>
    </view>
    <view class="vmb-swiper">
      <u-swiper border-radius="20" :list="swiperList"></u-swiper>
    </view>
    <view class="vmb-ad">
      <u-image width="100%" height="180rpx" :src="require('@/static/index/ad.gif')"></u-image>
    </view>
    <view class="vmb-grid">
      <u-grid :col="5" @click="click" hover-class="hover-class">
        <u-grid-item v-for="(item, index) in 10" :index="index" :key="index">
          <u-image width="80rpx" height="80rpx" :src="require('@/static/index/grid_'+item+'.png')"></u-image>
          <text class="grid-text">{{ '宫格' + (index + 1) }}</text>
        </u-grid-item>
      </u-grid>
    </view>
    <view class="vmb-waterfall">
      <u-waterfall v-model="flowList" ref="uWaterfall">
        <template v-slot:left="{leftList}">
          <view class="vmb-warter" v-for="(item, index) in leftList" :key="index">
            <!-- 警告：微信小程序不支持嵌入lazyload组件，请自行如下使用image标签 -->
            <!-- #ifndef MP-WEIXIN -->
            <u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index"></u-lazy-load>
            <!-- #endif -->
            <!-- #ifdef MP-WEIXIN -->
            <view class="vmb-img-wrap">
              <image class="vmb-image" :src="item.image" mode="widthFix"></image>
            </view>
            <!-- #endif -->
            <view class="vmb-title">
              {{item.title}}
            </view>
            <view class="vmb-price">
              {{item.price}}元
            </view>
            <view class="vmb-tag">
              <view class="vmb-tag-owner">
                自营
              </view>
              <view class="vmb-tag-text">
                放心购
              </view>
            </view>
            <view class="vmb-shop">
              {{item.shop}}
            </view>
            <!-- 微信小程序无效，因为它不支持在template中引入组件 -->
            <u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
          </view>
        </template>
        <template v-slot:right="{rightList}">
          <view class="vmb-warter" v-for="(item, index) in rightList" :key="index">
            <!-- #ifndef MP-WEIXIN -->
            <u-lazy-load threshold="-450" border-radius="10" :image="item.image" :index="index"></u-lazy-load>
            <!-- #endif -->
            <!-- #ifdef MP-WEIXIN -->
            <view class="vmb-img-wrap">
              <image class="vmb-image" :src="item.image" mode="widthFix"></image>
            </view>
            <!-- #endif -->
            <view class="vmb-title">
              {{item.title}}
            </view>
            <view class="vmb-price">
              {{item.price}}元
            </view>
            <view class="vmb-tag">
              <view class="vmb-tag-owner">
                自营
              </view>
              <view class="vmb-tag-text">
                放心购
              </view>
            </view>
            <view class="vmb-shop">
              {{item.shop}}
            </view>
            <!-- 微信小程序无效，因为它不支持在template中引入组件 -->
            <u-icon name="close-circle-fill" color="#fa3534" size="34" class="u-close" @click="remove(item.id)"></u-icon>
          </view>
        </template>
      </u-waterfall>
      <u-loadmore bg-color="rgb(240, 240, 240)" :status="loadStatus" @loadmore="addRandomData"></u-loadmore>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        searchShow: true,
        searchShow2: false,
        keyword: "",
        swiperList: [{
          image: require("../../static/index/swiper_1.jpg"),
        }, {
          image: require("../../static/index/swiper_1.jpg"),
        }, {
          image: require("../../static/index/swiper_1.jpg"),
        }, ],
        loadStatus: 'loadmore',
        flowList: [],
        list: [{
            price: 35,
            title: '北国风光，千里冰封，万里雪飘',
            shop: '李白杜甫白居易旗舰店',
            image: require("../../static/index/swiper_1.jpg"),
          },
          {
            price: 75,
            title: '望长城内外，惟余莽莽',
            shop: '李白杜甫白居易旗舰店',
            image: require("../../static/index/swiper_1.jpg"),
          },
        ]
      }
    },
    onLoad() {
      this.addRandomData();
    },
    onReachBottom() {
      this.loadStatus = 'loading';
      // 模拟数据加载
      setTimeout(() => {
        this.addRandomData();
        this.loadStatus = 'loadmore';
      }, 1000)
    },
    onPageScroll({
      scrollTop
    }) {
      if (scrollTop >= 50) {
        this.searchShow = false;
        this.searchShow2 = true;
      }
      if (scrollTop < 50) {
        this.searchShow = true;
        this.searchShow2 = false;
      }
    },
    methods: {
      addRandomData() {
        for (let i = 0; i < 10; i++) {
          let index = this.$u.random(0, this.list.length - 1);
          // 先转成字符串再转成对象，避免数组对象引用导致数据混乱
          let item = JSON.parse(JSON.stringify(this.list[index]))
          item.id = this.$u.guid();
          this.flowList.push(item);
        }
      },
      remove(id) {
        this.$refs.uWaterfall.remove(id);
      },
      clear() {
        this.$refs.uWaterfall.clear();
      }
    }
  }
</script>

<style lang="scss" scoped>
  .vmb {
    &-container {}

    &-search {
      padding: 0 25rpx;
      background: linear-gradient(to right, #ff6034, #ee0a24);
      height: 300rpx;
      border-radius: 0 0 50rpx 50rpx;
      width: 100%;
      position: fixed;


      ::v-deep {
        .u-navbar {
          background: transparent !important;
          box-shadow: none;
          border: 0;

          .u-title {
            color: #FFFFFF !important;
          }


        }

        .u-border-bottom:after {
          border-bottom-width: 0;
        }

        .u-action {
          color: #FFFFFF
        }
      }
    }

    &-search2 {
      padding: 25rpx ;
      background: linear-gradient(to right, #ff6034, #ee0a24);
      height: 110rpx;
      width: 100%;
      position: fixed;
      z-index: 999;

      ::v-deep {

        .u-action {
          color: #FFFFFF
        }
      }
    }

    &-swiper {
      padding: 180rpx 25rpx 25rpx 25rpx;
    }

    &-ad {
      padding: 0rpx 25rpx 25rpx 25rpx;
    }

    &-warter {
      border-radius: 8px;
      margin: 5px;
      background-color: #ffffff;
      padding: 8px;
      position: relative;
    }

    .u-close {
      position: absolute;
      top: 32rpx;
      right: 32rpx;
    }

    &-image {
      width: 100%;
      border-radius: 4px;
    }

    &-title {
      font-size: 30rpx;
      margin-top: 5px;
      color: $u-main-color;
    }

    &-tag {
      display: flex;
      margin-top: 5px;
    }

    &-tag-owner {
      background-color: $u-type-error;
      color: #FFFFFF;
      display: flex;
      align-items: center;
      padding: 4rpx 14rpx;
      border-radius: 50rpx;
      font-size: 20rpx;
      line-height: 1;
    }

    &-tag-text {
      border: 1px solid $u-type-primary;
      color: $u-type-primary;
      margin-left: 10px;
      border-radius: 50rpx;
      line-height: 1;
      padding: 4rpx 14rpx;
      display: flex;
      align-items: center;
      border-radius: 50rpx;
      font-size: 20rpx;
    }

    &-price {
      font-size: 30rpx;
      color: $u-type-error;
      margin-top: 5px;
    }

    &-shop {
      font-size: 22rpx;
      color: $u-tips-color;
      margin-top: 5px;
    }
  }
</style>
