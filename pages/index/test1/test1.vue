<template>
	<view>
		<button type="primary" @click="button1">开始人脸认证</button>
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
			}
		}
	}
</script>

<style>
	button {
		margin: 5px;
	}
</style>