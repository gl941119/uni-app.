<template>
    <view>
        <view class="page-body">
            <view class="page-section page-section-gap">
                <map style="width: 100%; height: 24rem;" :latitude="latitude" :longitude="longitude" :markers="covers">
                </map>
            </view>
        </view>
        <view class="bottom">
            <view class="bottom-info">
                <view></view>
                <span>我的位置</span>
                <span>不晓得哪个咔咔蝈蝈</span>
            </view>
            <view class="bottom-btn">
                <button type="primary">确定返校</button>
            </view>

        </view>
    </view>
</template>

<script>
  export default {
    name: 'backSchool',
    data() {
      return {
        title: 'map',
        latitude: 39.909,
        longitude: 116.39742,
        covers: [{
          latitude: 39.909,
          longitude: 116.39742,
          iconPath: '../../../static/location.png'
        }, {
          latitude: 39.90,
          longitude: 116.39,
          iconPath: '../../../static/location.png'
        }]
      }
    }
  }
</script>

<style scoped>

</style>
