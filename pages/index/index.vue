<template>
	<view class="uni-container">
		<view style="flex-wrap: wrap;disflex-direction: row; display: flex;">
		<text class="btn" @click="isDisableScreen(1)">
			禁止截屏
		</text>
		<text class="btn" @click="isDisableScreen(0)">
			允许截屏
		</text>
		<text class="btn" @click="getSignature()">
			获取应用签名
		</text>
		<text class="btn" @click="getApkSHA()">
			获取ApkSHA
		</text>
		<text class="btn" @click="checkIsRoot()">
			检查是否Root
		</text>
		
		</view>
	<view>
		签名：{{signature}}
		</br>
			sha1：{{sha}}
	</view>
	
	</view>
</template>
<script>
	var safeModule = uni.requireNativePlugin("Ionic-Safe");
	export default {
		data() {
			return {
				signature:"",
				sha:""
			}
		},
		onLoad() {},
		methods: {
			
			isDisableScreen(isDisable) {
				safeModule.isDisableScreen(isDisable, ret => {
					uni.showToast({
						title: ret,
						icon: 'none',
						position: 'bottom'
					});
				});
			},getSignature(){
				safeModule.getSignature(ret => {
					this.signature=ret.data;
					uni.showToast({
						title: ret,
						icon: 'none',
						position: 'bottom'
					});
				});
			},getApkSHA(){
				safeModule.getApkSHA(ret => {
					this.sha=ret.data;
					uni.showToast({
						title: ret,
						icon: 'none',
						position: 'bottom'
					});
				});
			},checkIsRoot(){
				safeModule.checkIsRoot(ret => {
					uni.showToast({
						title: ret,
						icon: 'none',
						position: 'bottom'
					});
				});
			}
		}
	}
</script>

<style>
	.uni-container{
		flex-direction: column;
		display: flex;
		justify-content: center;
	}
	.btn {
		font-size: 24rpx;
		padding:10px 8px;
		text-align: center;
		display: block;
		margin-top: 20px;
		background-color: #007AFF;
		color: #FFFFFF;
		margin-right: 10px;
		border-radius: 5px;
	}
</style>
