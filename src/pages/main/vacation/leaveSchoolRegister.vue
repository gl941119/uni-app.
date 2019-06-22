<template>
    <view class="stay-school-box">
        <form>
            <view class="form-item">
                <view class="title">假期离校类型</view>
                <picker @change="leaveTypeChange" :value="leaveType" :range="leaveTypeList" class="picker-box">
                    <view class="uni-input picker-input">{{leaveTypeList[leaveType]}}</view>
                </picker>
                <span class="uni-icon uni-icon-arrowright"></span>
            </view>
            <view class="form-item mrginTop">
                <view class="title">离校交通工具</view>
                <picker @change="trafficChange" :value="traffic" :range="trafficList" class="picker-box">
                    <view class="uni-input picker-input">{{trafficList[traffic]}}</view>
                </picker>
                <span class="uni-icon uni-icon-arrowright"></span>
            </view>
            <view class="form-item mrginTop">
                <view class="title">所在地区</view>
                <picker @columnchange="areaChange" :value="area" :range="areaList" mode="multiSelector"
                        class="picker-box">
                    <view class="uni-input picker-input">
                        {{areaList[0][area[0]]}}，{{areaList[1][area[1]]}}，{{areaList[2][area[2]]}}
                    </view>
                </picker>
                <span class="uni-icon uni-icon-arrowright"></span>
            </view>
            <view style="padding: 0 1rem;background: #fff;border-bottom: 1px solid #E3E3E3;">
                <view class="uni-title " >详细地址</view>
                <view class="uni-textarea">
                    <textarea auto-height placeholder-style="color:#C2C2C2" placeholder="请详细填写地址信息,如小区名门牌号等" style="padding: 0;min-height: 2rem"/>
                </view>
            </view>
            <view class="form-item mrginTop">
                <view class="title ">离校交通工具</view>
                <picker @change="trafficChange" :value="traffic" :range="trafficList" class="picker-box">
                    <view class="uni-input picker-input">{{trafficList[traffic]}}</view>
                </picker>
                <span class="uni-icon uni-icon-arrowright"></span>
            </view>
            <view class="form-item mrginTop">
                <view class="title">本人联系电话</view>
                <input class="uni-input" focus placeholder="本人联系电话" />
            </view>
            <view class="form-item">
                <view class="title">家庭联系电话</view>
                <input class="uni-input" focus placeholder="家庭联系电话" />
            </view>
        </form>
        <view class="footer-box">
            <button type="primary" size="small" class="login-btn" @click="submit">提交</button>
        </view>
    </view>
</template>

<script>
  import uniList from '@/components/uni-list/uni-list.vue'
  import uniListItem from '@/components/uni-list-item/uni-list-item.vue'

  export default {
    name: 'leave-school-register',
    components: {
      uniList,
      uniListItem
    },
    data() {
      return {
        leaveTypeList: ['回家', '旅游', '探亲', '其他'],
        trafficList: ['飞机', '火车', '汽车', '轮船', '其他'],
        leaveType: 0,
        traffic: 0,
        areaList: [
          ['四川', '北京'],
          ['成都市', '内江市', '达州市', '兰州市'],
          ['一环路', '二环路', '三环路']
        ],
        area: [0, 0, 0]
      }
    },
    methods: {
      async submit() {
        await uni.showToast({
          title: '登记成功',
          icon: {
            none: true
          },
          duration: 2000
        })
        uni.switchTab({url: '/pages/main/home/home'})
      },
      leaveTypeChange(e) {
        console.log('picker发送选择改变，携带值为：' + e.target.value)
        this.leaveType = e.target.value
      },
      trafficChange(e) {
        console.log('picker发送选择改变，携带值为：' + e.target.value)
        this.traffic = e.target.value
      },
      areaChange(e) {
        debugger
        console.log('修改的列为：' + e.detail.column + '，值为：' + e.detail.value)
        this.area[e.detail.column] = e.detail.value
        // this.area = e.target.value
      }
    }
  }
</script>

<style scoped lang="less">
    .stay-school-box {
        padding: 1rem 0;
        .form-item {
            padding: 0 1rem;
            background: #fff;
            border-bottom: 1px solid #E3E3E3;
            display: flex;
            align-items: center;
            .title {
                width: 4.5rem;
            }
            input {
                padding-left: 1rem;

            }
        }
        .mrginTop {
            margin-top: .5rem;
        }
        .footer-box {
            position: fixed;
            width: 100%;
            background: #fff;
            bottom: 0;
            padding: .8rem 0;
        }
        .login-btn {
            width: 80%;
            background: #252577;
            border-radius: 3rem;
        }
        .picker-input {
            display: inline-block;
        }
        .uni-icon-arrowright {
            font-size: 12px;
        }
        .picker-box {
            width: 70%;
            text-align: right;
        }
    }
</style>
