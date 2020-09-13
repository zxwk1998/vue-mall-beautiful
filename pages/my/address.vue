<template>
  <view>
    <view class="item" v-for="(res, index) in siteList" :key="res.id">
      <view class="top">
        <view class="name">{{ res.name }}</view>
        <view class="tag">
          <text v-for="(item, index) in res.tag" :key="index" :class="{red:item.tagText=='默认'}">{{ item.tagText }}</text>
        </view>
      </view>
      <view class="bottom">
        <view class="phone">{{ res.phone }}</view>
        {{res.site}}
        <u-icon @tap="toAddSite" name="edit-pen" :size="40" color="#999999"></u-icon>
      </view>
    </view>
    <view class="addSite" @tap="toAddSite">
      <view class="add">
        <u-icon name="plus" color="#ffffff" class="icon" :size="30"></u-icon>新建收货地址
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        siteList: []
      };
    },
    onLoad() {
      this.getData();
    },
    methods: {
      getData() {
        this.siteList = [{
          id: 1,
          name: 'vue-mall-beautiful',
          phone: '183****5523',
          tag: [{
              tagText: '默认'
            },
            {
              tagText: '家'
            }
          ],
          site: '广东省深圳市宝安区 自由路66号'
        }, {
          id: 1,
          name: 'vue-mall-beautiful',
          phone: '183****5523',
          tag: [{
              tagText: '默认'
            },
            {
              tagText: '家'
            }
          ],
          site: '广东省深圳市宝安区 自由路66号'
        }, {
          id: 2,
          name: 'vue-mall-beautiful',
          phone: '183****5523',
          tag: [{
              tagText: '默认'
            },
            {
              tagText: '家'
            }
          ],
          site: '广东省深圳市宝安区 自由路66号'
        }];
      },
      toAddSite() {
        uni.navigateTo({
          url: '/pages/my/addSite'
        });
      }
    }
  };
</script>

<style lang="scss" scoped>
  .item {
    padding: 40rpx 20rpx;

    .top {
      display: flex;
      font-weight: bold;
      font-size: 34rpx;

      .phone {
        margin-left: 60rpx;
      }

      .tag {
        display: flex;
        font-weight: normal;
        align-items: center;

        text {
          display: block;
          width: 60rpx;
          height: 34rpx;
          line-height: 34rpx;
          color: #ffffff;
          font-size: 20rpx;
          border-radius: 6rpx;
          text-align: center;
          margin-left: 30rpx;
          background-color: rgb(49, 145, 253);
        }

        .red {
          background-color: red
        }
      }
    }

    .bottom {
      display: flex;
      margin-top: 20rpx;
      font-size: 28rpx;
      justify-content: space-between;
      color: #999999;
    }
  }

  .addSite {
    display: flex;
    justify-content: space-around;
    width: 600rpx;
    line-height: 100rpx;
    position: absolute;
    bottom: 30rpx;
    left: 80rpx;
    background: linear-gradient(to right, #ff6034, #ee0a24);
    border-radius: 60rpx;
    font-size: 30rpx;

    .add {
      display: flex;
      align-items: center;
      color: #ffffff;

      .icon {
        margin-right: 10rpx;
      }
    }
  }
</style>
