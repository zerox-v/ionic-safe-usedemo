<template>
	<view class="uni-container">
		<view style="flex-wrap: wrap;disflex-direction: row; display: flex;">
			<text class="btn" @click="doany(1)">
				禁止截屏
			</text>
			<text class="btn" @click="doany(2)">
				允许截屏
			</text>
			<text class="btn" @click="doany(3)">
				获取应用签名
			</text>
			<text class="btn" @click="doany(4)">
				获取ApkSHA
			</text>
			<text class="btn" @click="doany(9)">
				检测是否root
			</text>
			<text class="btn" @click="doany(5)">
				检测是否调试模式
			</text>
			<text class="btn" @click="doany(6)">
				检测进程是否被追踪
			</text>
			<text class="btn" @click="doany(7)">
				检测是否有Wifi代理
			</text>
			<text class="btn" @click="doany(8)">
				检测检测动态调试
			</text>
			<text class="btn" @click="doany(10)">
				检测是否是模拟器
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
				signature: "",
				sha: "",
			};
		},
		onLoad() {},
		methods: {
			doany(i) {

				switch (i) {
					case 1:
						safeModule.isDisableScreen(1, (res) => {
							this.showToast(res);
						})
						break;
					case 2:
						safeModule.isDisableScreen(0, (res) => {
							this.showToast(res);

						})
						break;
					case 3:
						safeModule.getSignature((res) => {
							this.signature = res.data;
							this.showToast(res.state);

						})
						break;
					case 4:
						safeModule.getApkSHA((res) => {
							this.sha = res.data;
							this.showToast(res.state);
						})
						break;
					case 5:
						safeModule.isDebuggable((res) => {
							this.showToast(res);

						})
						break;
					case 6:
						safeModule.isUnderTraced((res) => {
							this.showToast(res);

						})
						break;
					case 7:
						safeModule.isWifiProxy((res) => {
							this.showToast(res);
						})
						break;
					case 8:
						safeModule.detectedDynamicDebug();
						break;
					case 9:
						safeModule.checkIsRoot((res) => {
							this.showToast(res);

						})
						break;
					case 10:
						safeModule.isEmulator((res) => {
							this.showToast(res);

						})
						break;

				}

			},
			showToast(text) {
				uni.showToast({
					title: text,
					icon: "none",
					position: "bottom",
				});
			},

		},
	};
</script>

<style>
	.uni-container {
		flex-direction: column;
		display: flex;
		justify-content: center;
	}

	.btn {
		font-size: 24rpx;
		padding: 10px 8px;
		text-align: center;
		display: block;
		margin-top: 20px;
		background-color: #007aff;
		color: #ffffff;
		margin-right: 10px;
		border-radius: 5px;
	}
</style>
