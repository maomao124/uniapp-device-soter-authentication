<template>
	<view>
		<button type="primary" @click="button1">开始人脸认证</button>
		<button type="primary" @click="button2">开始指纹识别</button>
		<button type="primary" @click="button3">获取本机支持的生物认证方式</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			button1() {
				console.log("人脸认证");
				uni.startSoterAuthentication({
					requestAuthModes: ['facial'],
					challenge:'12345',
					authContent: '请人脸认证',
					success: (data) => {
						console.log("生物认证方式:" + data.authMode);
						console.log('resultJSON:' + data.resultJSON);
						console.log("resultJSONSignature:" + data.resultJSONSignature);
					},
					fail: (err) => {
						console.log("错误码：" + err.errCode);
						console.log("错误信息：" + err.errMsg);
					}
				})
			},
			button2() {
				console.log("指纹识别");
				uni.startSoterAuthentication({
					requestAuthModes: ['fingerPrint'],
					challenge:'12345',
					authContent: '请指纹认证',
					success: (data) => {
						console.log("生物认证方式:" + data.authMode);
						console.log('resultJSON:' + data.resultJSON);
						console.log("resultJSONSignature:" + data.resultJSONSignature);
					},
					fail: (err) => {
						console.log("错误码：" + err.errCode);
						console.log("错误信息：" + err.errMsg);
					}
				})
			},
			button3()
			{
				console.log("获取本机支持的生物认证方式");
				uni.checkIsSupportSoterAuthentication({
					success: (data) => {
						console.log('支持：',data.supportMode);
						uni.showModal({
							showCancel:false,
							title:'提示',
							content:'支持：'+data.supportMode
						})
					},
					fail: (err) => {
						console.log("错误:",err);
					}
				})
			}
		}
	}
</script>

<style>
	button {
		margin: 5px;
	}
</style>