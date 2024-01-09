<template>
<view class="page-container">
</view>
</template>
<script lang="ts">
export default {
name: 'indexPage'
};
</script>
<script lang="ts" setup>
/* eslint-disable no-undef */
import { onLoad, onReady, onShow, onPullDownRefresh, onReachBottom } from '@dcloudio/uni-app';
import { ref, Ref, computed, watch } from 'vue';
import { storeToRefs } from 'pinia';
import { usePointStore } from '@/store/point';
import { useUserStore } from '@/store/user';
import { track } from '@/common/tLog';
import { goMenuPage } from '@/utils/index';


/** 获取store的数据 **/
const { point } = storeToRefs(usePointStore());
const userStore = useUserStore();


/** 接收父组件数据 **/
const props = defineProps({
parentData: Number,
});


/** 定义一些响应式变量 **/
const alias1: Ref<number> = ref(0);


/** 定义计算属性值 */
const aliasComputed = computed(() => alias1.value + 1);


/** 监听变量值 **/
watch(
() => point.value.pointId,
val => val && initRequest()
);


/** 页面加载 **/
onLoad((options) => {
// 打点
track('track_name', 'track_value');
console.log('接收链接参数:', options);
console.log('point:', point.value);
console.log('userStore:', userStore);
console.log('parentData:', props.parentData);
});


/** 启动生命周期 **/
onReady(() => {
//
});


/** 页面显示 **/
onShow(() => {
initRequest();
});


/** 页面下拉 **/
onPullDownRefresh(() => {
console.log('页面下拉');
});


/** 页面上拉 **/
onReachBottom(() => {
console.log('页面上拉');
});


/** 请求页面数据 **/
const initRequest = () => {};


/** 跳转页面-支持webview */
// goMenuPage('/pages/home/index');


/** 定义组件暴露给父组件的方法 **/
defineExpose({ initRequest });
</script>
<style lang="scss" scoped>
page {
background-color: #fff;
}
.page-container {
width: 100%;
}
</style>
