<template>
    <view class="vacation-detail-page">
        <view class="vacation-detail-basic">
            <view class="vacation-title">
                <h3 class="title">2019春节放假通知</h3>
                <uniTag text="登记中" type="success" :circle="true" size="small" :inverted="true" class="tag-box"></uniTag>
            </view>
            <view class="vacation-publish-time">
                <p>发布时间：2019-02-01 12:00:00</p>
            </view>
            <view class="vacation-time">
                <p><span>开始时间：</span><span>2019-01-31 12:00:00</span></p>
                <p><span>结束时间：</span><span>2019-02-03 12:00:00</span></p>
                <p><span>假期时长：</span><span>3天0小时</span></p>
            </view>
            <view class="vacation-tips">在假期登记结束前你可以重新提交，重新提交将自动覆盖上次提交的内容</view>
        </view>
        <view class="vacation-attention">
            <h3 class="attention-title">假期注意事项</h3>
            <view class="attention-content">
                <view>
                    夏天要用的电器真不少，孩子一个人在家难免要烧个水热个饭，空调风扇也都是需要用电的。那么用电常识一定要告知孩子，湿手的时候千万不要触碰夏天要用的电器真不少，孩子一个人在家难免要烧个水热个饭，空调风扇也都是需要用电的。那么用电常识一定要告知孩子夏天要用的电器真不少，孩子一个人在家难免要烧个水热个饭，空调风扇也都是需要用电的。那么用电常识一定要告知孩子夏天要用的电器真不少，孩子一个人在家难免要烧个水热个饭，空调风扇也都是需要用电的。那么用电常识一定要告知孩子夏天要用的电器真不少。
                </view>
                <view class="isRead">
                    <checkbox-group @change="changeRadio">
                        <checkbox color="#09BB07" :checked="hasRead">我已阅读<span>《假期注意事项》</span></checkbox>
                    </checkbox-group>
                </view>
                <!-- <view class="content-more">
                    <view>...</view>
                    <view class="open" @click="openText">展开</view>
                </view> -->
            </view>
        </view>
        <view class="navigator-box" v-if="type===0">
            <view class="navigate-item" @click="leaveRegister">
                <view>离校登记</view>
            </view>
            <view class="navigate-item" @click="stayRegister">
                <view>留校登记</view>
            </view>
        </view>
        <view class="navigator-box" v-else-if="type===1">
            <view class="navigate-again" @click="againRegister">
                <view>重新登记</view>
            </view>
        </view>
        <view class="navigator-box" v-else>
            <view class="navigate-again" @click="backRegister">
                <view>返校登记</view>
            </view>
        </view>
        <uni-popup :show="showTip" position="middle" mode="fixed">
            <view class="popup-content">
                <h3>提示</h3>
                <view class="content">
                    请先勾选我已阅读《假期注意事项》
                </view>
                <view class="sure-button" @click="sure">
                    <view class="sure">确定</view>
                </view>
            </view>
        </uni-popup>
    </view>
</template>

<script>
  import uniTag from '@/components/uni-tag/uni-tag.vue'
  import uniPopup from '@/components/uni-popup/uni-popup.vue'

  export default {
    name: 'detail',
    components: {
      uniTag,
      uniPopup
    },
    data() {
      return {
        hasRead: false,
        showTip: false,
        type: 3,
        isShowTip : (callback)=> {
          if (this.hasRead) {
            callback()
          } else {
            this.showTip = true
          }
        }
      }
    },
    methods: {
      changeRadio() {
        this.hasRead = !this.hasRead
      },
      leaveRegister() { // 离校登记
        this.isShowTip(()=>{
          uni.navigateTo({url: '/pages/main/vacation/leaveSchoolRegister'})
        })
      },
      stayRegister() { // 留校登记
        this.isShowTip(()=>{
          uni.navigateTo({url: '/pages/main/vacation/staySchoolRegister'})
        })
      },
      againRegister() { // 重新登记
        this.isShowTip(()=>{
          // this.type=== 2   ? uni.navigateTo({url: '/pages/main/vacation/leaveSchoolRegister'}) : uni.navigateTo({url: '/pages/main/vacation/staySchoolRegister'})
        })
      },
      backRegister() { // 返校登记
       this.isShowTip(()=>{
         uni.navigateTo({url: '/pages/main/vacation/backSchool'})
       })
      },
      sure() { // 关闭提示弹框
        this.showTip = false
      },
    }

  }
</script>

<style scoped lang="less">
    .vacation-detail-page {
        height: 100%;

        .vacation-detail-basic {
            padding: 1rem;
            background: #fff;

            .vacation-title {
                display: flex;
                align-items: center;

                .title {
                    font-size: 1rem;
                }

                .tag-box {
                    margin-left: 1rem;
                }
            }
        }

        .vacation-time {
            padding: 1rem 0;
            font-size: .9rem;

            p {
                span:first-of-type {
                    color: #999;
                }
            }
        }

        .vacation-tips {
            padding: 1rem;
            background: #F4F4F8;
            border-radius: .3rem;
            color: #999999;

            &::before {
                content: "";
                position: absolute;
                height: 2rem;
                width: .2rem;
                background: #F39539;
                left: 1rem;
                margin-top: .3rem;
            }
        }

        .vacation-attention {
            margin-top: 1rem;
            margin-bottom: 2rem;
            padding: 1rem;
            background: #fff;

            .attention-title {
                font-size: .9rem;
            }

            .attention-content {
                width: 100%;
            }

            .isRead {
                padding: 1rem 0;

                span {
                    color: #252577
                }
            }

            .content-more {
                position: absolute;
                /* margin-top: -1rem; */
                display: flex;
                background: #fff;
                right: 1rem;
                margin-top: 2.7rem;

                .open {
                    padding-left: .2rem;
                    color: #252577
                }
            }
        }

        .navigator-box {
            display: flex;
            position: fixed;
            z-index: 9;
            bottom: 0;
            background: #fff;
            width: 100%;
            border-top: 1px solid #E3E3E3;

            .navigate-item {
                width: 50%;
                padding: .5rem;
                text-align: center;
                color: #252577;

                &:first-of-type {
                    border-right: 1px solid #E3E3E3;
                }
            }
            .navigate-again {
                width: 100%;
                padding: .5rem;
                text-align: center;
                color: #252577;
            }
        }

        // 		.popup-box {
        // 			background: #fff;
        // 		}
        .popup-content {
            width: 100%;
            text-align: center;
            .content {
                text-align: left;
                padding: 1rem 0;
            }
        }
        .sure-button {
            padding-top: 1rem;
            border-top: 1px solid #E3E3E3;
            .sure {
                color: #00C200;
                font-size: .9rem
            }
        }
    }
</style>
